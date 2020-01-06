---
title: "2019 abletech"
date: 2020-01-06T11:16:32+13:00
draft: true
type: "cover letter"
print-title: "abletech"
homepage: "hanswustrack.com"
email: "hans.wustrack@gmail.com"
phone-number: "022-580-0127"
location: "Wellington, New Zealand"
---

Dear Hiring Manager,

I am a highly motivated Software Developer who deeply enjoys working on an agile team and developing streamlined documented processes to make that team efficient and effective. With my background in tech support, I have also come to love speaking directly with customers and bringing those learnings back to the development team. After working in tech support, I transitioned to a software development position where I built highly scalable data services using .NET technologies.

I am eager to speak with you more about the opening for Junior Ruby Developer Internship at abletech and how I can contribute to your continued success.

See below for my qualifications and FizzBuzz implementation.

{{< cover-letter-closing "Best regards," "Hans Wustrack" >}}

**Advertised Requirements**|**My Qualifications**
:-----:|:-----:
Familiarity with web development|I have experience maintaining an ASP.NET web application that was used for my previous company's legacy cloud platform.
Comfortable with a back-end programming language|In my previous position, my main focus was on writing backend microservices written in .NET and running on Azure's Service Fabric platform.
Familiarity with relational databases|Our microservices stored metadata in Azure SQL. I designed and benchmarked the schema when converting from Azure Table Storage to Azure SQL.
Agile mindset and collaborative approach|In my previous position, we used a scrum process to keep the team lean and agile. I took charge in work planning sessions and writing up work items for future work.
Willingness to learn and a can-do attitude|At my previous company, I started in Tech Support and eventually moved to Software Development. This was all based on my efforts to learn development and grow my skills outside of work.
Must be a NZ resident and have a good level of written and spoken English|I'm currently living in Wellington on a Work Holiday Visa. This allows me to accept short term employment. I'm from the United States, so fluent in English.
Must have a relevant qualification such as a Computer Science degree, EDA qualification or similar|I have a BS in Mechanical Engineering, certificate in CS, and previous work experience as a software developer. 
 
**Advertised Preferred Qualifications**| 
:-----:|:-----:
Experience with Ruby/Rails|I do not have any experience with Rails but really admire Basecamp, so would love to dive in on this framework.
Experience with building APIs|I have experience building APIs with ASP.NET and ASP.NET core.
Understanding of object-oriented programming|My professional experience is all with .NET so I have a strong understand of OOP.
Understanding of event-driven architecture and microservices|My team was working on microservices running in Azure, so I have direct experience with this.
Some knowledge of front-end technologies such as HTML and Javascript|I have designed and built websites for personal projects that use the Hugo static site generator and have custom HTML, CSS, and JS.

```csharp
public static void Main()
{
    for (int i = 1; i <= 100; i++)
    {
        string output = "";
        output += (i % 3 == 0) ? "Fizz" : "";
        output += (i % 5 == 0) ? "Buzz" : "";
        Console.WriteLine(output == "" ? i.ToString() : output);
    }
}
```