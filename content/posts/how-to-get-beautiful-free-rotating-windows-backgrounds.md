---
title: "How to Get Beautiful Free Rotating Windows Backgrounds"
date: 2020-02-16T14:10:53+13:00
draft: true
---

[Unsplash](https://unsplash.com/) is a great resource for free, high-quality, images. After seeing [this blog post](https://thenextweb.com/basics/2019/07/05/how-to-grab-beautiful-free-wallpapers-for-your-iphone-or-ipad-with-a-quick-shortcut/) outlining how to automatically get a great background photo for your iPhone or iPad, I wanted to try the same my Windows laptop.

**TLDR**
- Sign up for the [Unsplash API](https://unsplash.com/developers) and save your access key in credential manager under the name 'unsplash'.
- Set [this PowerShel](https://github.com/hwustrack/GetUnsplashWallpaperPs) script to run as a scheduled task. It will download a random photo from Unsplash and save it to the local directory.
- Set your Windows background as a slideshow with the directory you put the PowerShel script in as the album.

# Background
I've really liked Windows Spotlight since it was introduced. Who wouldn't want an endless series of beautiful images on your lock screen? Unfortunately, this  isn't officially supported for updating your background, only your lock screen. After seeing [this blog post](https://thenextweb.com/basics/2019/07/05/how-to-grab-beautiful-free-wallpapers-for-your-iphone-or-ipad-with-a-quick-shortcut/) outlining how to automatically get a great background photo for your iPhone or iPad, I knew I wanted to set this up on my laptop.

# Getting started
- Sign up for a free developer account on the [Unsplash developer portal](https://unsplash.com/developers) to get API access.
- Create an application in the portal and copy the Access Key value.
- Save the Access Key in Windows Credential Manager so it's safe but available to our script. Create a Generic Windows Credential in Credential Manager.
  - Set the 'Internet or network address' to 'unsplash'.
  - Add anything for 'User name', we won't use this value.
  - Paste the Access Key you copied into the Password field

# Script
The first thing we'll do is import the credential we created in getting started:
```ps1
$creds = Get-StoredCredential -Target unsplash
$access_key = $creds.GetNetworkCredential().password
```
To run the `Get-StoredCredential` cmdlet, we'll need the CredentialManager module. You can install that in PowerShell with `Install-Module -Name CredentialManager`.

Next, configure the parameters for the request we'll make to Unsplash:
```ps1
$collections = "437035,3652377,8362253"

$baseUrl = "https://api.unsplash.com"
$randomPhotoUrl = $baseUrl + "/photos/random"
$headers = @{ "Accept-Version" = "v1"; Authorization = "Client-ID $access_key" }
$params = @{ collections = $collections; orientation = "landscape" }
```
Unsplash's API lets you get random photos based on optional of parameters. Here, we provide a set of collections the photo should be chosen from and specify the orientation should be landscape. Collections are a user created group of photos. I selected a few random collections by browsing through the top nature ones. Browse to find your favorite wallpaper collections [here](https://unsplash.com/wallpapers).

The rest of this code is just setting up the HTTP request and parameters for getting the random photo.

Now we're ready to make the HTTP request. We'll actually make 3 requests: get a random photo's metadata, retrieve that photo in a specific size and format, and finally, tell Unsplash that we've downloaded the photo:
```ps1
$response = Invoke-WebRequest $randomPhotoUrl -Method Get -Headers $headers -Body $params
$content = $response | ConvertFrom-Json
$imgUrl = $content.urls.raw
$id = $content.id
Invoke-WebRequest $imgUrl -Headers $headers -Body @{ fm = "jpg"; w = "1920"; q = "80" } -OutFile ".\$id.jpg"
Invoke-WebRequest "$baseUrl/photos/$id/download" -Headers $headers
```
The API is flexible and let's you supply parameters like the size and format of the picture to be returned. They use Imgix under the hood, so it's pretty flexible. You can see a list of supported parameters [here](https://unsplash.com/documentation#supported-parameters). My laptop's resolution is 1920 x 1080, so that's the size I ask for.

Unsplash [asks](https://help.unsplash.com/en/articles/2511258-guideline-triggering-a-download) that you make a request to the download endpoint after you've downloaded a photo, so they can keep an accurate count. So we do that last.

The photo has now been downloaded to the directory with the script. We'll output a metadata file with info about the photo in case we're curious about the location of the photo or who uploaded it.
```ps1
$sel = $content | 
    Select-Object @{n = "link"; e = { $_.links.html } }, @{n = "name"; e = { $_.user.name } }, 
        description, @{n = "location"; e = { $_.location.title } }, @{n = "retrieval time"; e = { Get-Date } }
$sel | Format-List | Out-File -FilePath ".\$id.txt"
```

Finally, we'll clean up old files so the directory doesn't fill up unnecessary disk space.
```ps1
Get-ChildItem -Path .\* -Include ("*.jpg", "*.txt") | Where-Object {$_.CreationTime -lt (Get-Date).AddMinutes(-60)} | Remove-Item
```
This will delete any photo and text file older than 60 minutes.

Now we have a script that will download a random photo in the size we want. Next we'll configure this to run periodically and for Windows to use photos from this directory as the background.

# Configuration

- Set the script to run periodically as a scheduled task: https://blog.netwrix.com/2018/07/03/how-to-automate-powershell-scripts-with-task-scheduler/
- Set your Windows background as a Slideshow with the script directory as the album: https://www.windowscentral.com/enable-windows10-slideshow-and-battery

# Finishing up
It's awesome that Unsplash offers these photos completely for free and has a flexible API. I did have a hard time finding the collections I would want a photo from, so it'd be nice if you could filter based on the categories on the homepage (e.g. Wallpapers, Textures & Patterns, Nature, etc.), but once you've found the collections you like, everything else was straightforward.

Find the full PowerShell script on [GitHub](https://github.com/hwustrack/GetUnsplashWallpaperPs).
Find the full Unsplash API documentation [here](https://unsplash.com/documentation).