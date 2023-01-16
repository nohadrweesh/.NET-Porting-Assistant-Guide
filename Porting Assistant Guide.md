# The Story of .NET 

- .NET Core is a free, open-source, general-purpose development platform to build cloud-based software applications on Windows, Linux, and macOS whereas Microsoft’s .Net Framework is a software development platform for building and running Windows applications.
  
- .NET framework was released at 2002 and it only runs on Windows ,then Microsoft released .NET Core at 2016  that's cross platform but it's not completely compatible with the .NET framework apis.
   
- The last version of .NET framework was 4.8 and was released at 2019 and Microsoft continued with .NET Core but rebranded into the new name `.NET`

![alt .NET development timeline](images/dotnet_story_01.png ".NET development timeline")

## Challenges moving from .NET framework to .NET
- Incompatible .NET API calls
- Incompatible NuGet packages
- Difficultiy in assessing .NET portability
- Manual work in porting to .NET
# Description
- Porting Assistant for .NET is an analysis tool that scans .NET Framework applications and generates a .NET Core compatibility assessment, helping you port your applications to Linux faster. Porting .NET Framework applications to .NET Core helps customers take advantage of the performance, cost savings, and robust ecosystem of Linux. However, porting applications to .NET Core can be a significant manual effort. Application owners need to spend valuable time identifying the dependencies and APIs that are incompatible with .NET Core, and estimating the level of effort involved. Porting Assistant for .NET quickly scans .NET Framework applications to identify incompatibilities with .NET Core, finds known replacements, and generates a detailed compatibility assessment. This reduces the manual effort involved in modernizing your applications to Linux .
    
## Get .NET Porting Assistant 
- Porting Assistant for .NET is fully open-sourced.
- You can use the Porting Assistant in any of these flavors:
    -   [Standalone client](https://aws.amazon.com/porting-assistant-dotnet/) 
    -   [Visual Studio IDE extension](https://marketplace.visualstudio.com/items?itemName=AWSPA.AWSPortingAssistant2022) 
## Prerequisites
- .NET 6 SDK Download from [here](https://dotnet.microsoft.com/en-us/download/dotnet)
- Windows 7 or later
- Internet connectivity on the machine running the assessment
- If your machine is behind a proxy with restricted internet access, you must permit access to the following:
    - [Amazon S3 Datastore](https://s3.us-west-2.amazonaws.com/aws.portingassistant.dotnet.datastore/)
    - [Amazon S3 Datastore authenticaiton endpoint]( https://encore-telemetry.us-east-1.amazonaws.com/)
    - [GitHub datastore](https://github.com/aws/porting-assistant-dotnet-datastore/tree/master/data)
    - [GitHub user content](http://raw.githubusercontent.com/)
    - NuGet or additional package addresses — any addresses required to restore your project packages (the most common one being api.nuget.com)

- Administrator access
- Processor with 1.8 GHz or above processing speed
- 4 GB minimum of available memory (We would need higher memory requirments as long as the solution is larger)
- 5 GB minimum of free disk space
  
# Demo Workflow

- I will use the Porting Assistant Stanalone Client to assess and port [Music Store App](https://github.com/sagulati/MvcMusicStore/tree/net48-upgrade-completed) from .NET framework to .NET .

## Installation
- Download and Install the .NET Porting Assistant from [here](https://aws.amazon.com/porting-assistant-dotnet/)

## Assess The Solution
- Open the porting assistant
- Click on `Getting Started` Button 
 ![alt Porting Assistant Getting Started](images/porting_assistant_getting_started.PNG "Porting Assistant Getting Started")
- You should see `Assess New Solution` Page or Click on `Assess a New Solution` button to view it 
 ![alt Porting Assistant Assess Solution](images/porting_assistant_asses_solution.PNG "Porting Assistant Assess Solution")
- Click on `Choose file` and locate the solution file of your project that you want to modernize ,it must be a `.sln` file
- The porting assistant will start scanning and analyzing the application
![alt Porting Assistant Assessing In Progress](images/porting_assistant_assessing_in_progress.PNG "Porting Assistant Assessing In Progress")
- Wait for some time till the porting assistant finishes assessing the app, this time depends on the size of the application
![alt Porting Assistant Assessing Completed](images/porting_assistant_assessing_completed.PNG "Porting Assistant Assessing Completed")
- Let's review the assessed solution 
- Click on the solution name from the `Assessed Solutions` page
- You would see the Assessment overview at the top of the page, with statistics about :
    - Incompatible NuGet packages
    - Incompatible APIs
    - Build errors
    - Porting Actions
![alt Porting Assistant Assessment Overview](images/porting_assistant_project_overview.PNG "Porting Assistant Assessment Overview")
- At the bottom of the page you would see:
    - Included Projects summary with brief about each project including:
        - Framework Version
        - Referenced Projects
        - Incompataible packages
        - Incompatabile APIs
        - Build errors
        - Porting Actions
        - Port Status
         
      ![alt Porting Assistant Projects](images/porting_assistant_project_details.PNG "Porting Assistant Projects")

    - Project Reference Graph ,which shows the dependency graph of the included project in the solution
    ![alt Porting Assistant Project Reference](images/porting_assistant_project_reference_graph.PNG "Porting Assistant Project Reference")

    - NuGet Packages with some information about the used packages in the solution including:
        - Name
        - Version
        - Projects (Number of projects in which this package is used)
        - Source Files (Number of files in which this package is used)
        - APIs (Number of apis used from this package )
        - Status (Either compatible or Incompatible)
        - Suggested Replacement (Suggested package version to replace the used package with )  
             
      ![alt Porting Assistant NuGet Packages](images/porting_assistant_nuget_packages.PNG "Porting Assistant NuGet Packages")

    - APIs with some information about the used apis in the solution including:
        - Name
        - Package
        - Source Files (Number of files in which this api is used)
        - Calls (Number of calls to this api )
        - Status (Either compatible or Incompatible)
        - Suggested Replacement (Suggested api to replace the used api with)        
         
      ![alt Porting Assistant APIs](images/porting_assistant_project_apis.PNG "Porting Assistant APIs")

    - Source Files with some information about the used files in the solution including:
        - Source File Name
        - Incompatible API calls (Statistics about `Number of incompatible api calls / Total number of api calls` used in the file)     
         
      ![alt Porting Assistant Source Files](images/porting_assistant_project_source_files.PNG "Porting Assistant Source Files")

- You could click on the file name from `Source Files` or select the file and click on `View Details` to view the file with the Porting Assistant notes and recommendations
![alt Porting Assistant Source File 01](images/porting_assistant_project_source_files_example_01.PNG "Porting Assistant Source File 01")

  ![alt Porting Assistant Source File 02](images/porting_assistant_project_source_files_example_02.PNG "Porting Assistant Source File 02")

## Port the solution
- The Porting Assistant can help you porting the application by applying some porting actions like upgrading packages , replacing incompatible api calls,..etc but there still some actions that needs to be done manually and you could use the Porting Assistant to help identify those actions . 
- Click on the solution name from the `Assessed solutions` page and click on `Port Solution` Button , Then choose Either to Modify in place or Copy to new location and choose the location path 
![alt Porting Assistant Port Solution](images/porting_assistant_assesed_solution_porting.PNG "Porting Assistant Port Solution")
- You will be directed to a page where you can view some porting settings and NuGet packages upgrade
![alt Porting Assistant Porting Settings](images/porting_assistant_assesed_solution_porting_01.PNG "Porting Assistant Porting Settings")
![alt Porting Assistant Porting Packages Upgrade](images/porting_assistant_assesed_solution_porting_02.PNG "Porting Assistant Porting Packages Upgrade")
- Then the porting Assistant will start porting your solution automatically
![alt Porting Assistant Porting in Progress](images/porting_assistant_assesed_solution_porting_in_progress.PNG "Porting Assistant Porting in Progress")
- After Porting is completed , it will automatically start assessing the ported solution and you will see the ported solution in the `Assessed Solutions` 
![alt Porting Assistant Assessing In Progress After Porting](images/porting_assistant_assesed_solution_porting_assessing_in_progress.PNG "Porting Assistant Assessing In Progress After Porting")
- Wait for some time till the ported solution is fully assessed
![alt Porting Assistant Assessing Completed After Porting](images/porting_assistant_assesed_solution_porting_assessing_completed.PNG "Porting Assistant Assessing Completed After Porting")

- As you could see the Porting Assistant has already helped in porting most of the incompatibilities but not all of them ,we still need some manual actions to complete porting the app and you could use the Porting Assistant to locate the rest of incompatibilities.
  
- You can get more on the needed manual porting actions for this app by checking the [ASP.NET Migration Workshop](https://winonaws.cloud/dotnet/framework-to-core/5-intro.html)


# Resources
- [Porting Assistant for .NET Documentation](https://aws.amazon.com/porting-assistant-dotnet/)
- [Port .NET applications from .NET Framework to .NET Core | AWS Events](https://www.youtube.com/watch?v=JDGc6-v-yPA)
- [Porting Assistant Prerequisites](https://docs.aws.amazon.com/portingassistant/latest/userguide/porting-assistant-prerequisites.html)