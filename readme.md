



# Generate LivingDoc HTML file from Reqnroll Unit Tests



Install NuGet databinding.LivingDoc.ExecutionDataCollector in your Reqnroll test project.



Add file reqnroll.json at root path of the Reqnroll test project with this content :

```json
{
  "$schema": "https://schemas.reqnroll.net/reqnroll-config-latest.json",
  "bindingAssemblies": [
  ],
  "livingDocExecutionDataCollector": {
    "enabled": true,
    "filepath": "TestExecution.json"
  }
}
```



With these additions, we enable the generation of a TestExecution.json file in the test execution folder, containing test results in json format.



Now we have to install the SpecFlow LivingDoc CLI tool, in the terminal, execute : 

```batch
dotnet tool install --global SpecFlow.Plus.LivingDoc.CLI
```



Now, we can generate the HTML file. 

So, first, we need to execute unit tests, in the folder where is the csproj : 

```batch
dotnet test
```



And now, execute at the same location, the following command  :

```batch
livingdoc feature-folder . --output-type HTML -t bin/Debug/net8.0/TestExecution.json
```



The LivingDoc.html file should be generated in the same folder where you are located.




