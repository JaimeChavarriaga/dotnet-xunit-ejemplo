## Seleccionar pruebas en línea de comandos

Es posible limitar las pruebas a ejecutar usando dotnet test --filter

- https://learn.microsoft.com/en-us/dotnet/core/testing/selective-unit-tests?pivots=xunit#xunit-examples
- https://learn.microsoft.com/en-us/dotnet/core/tools/dotnet-test#filter-option-details


dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)|Priority=1"

| Opciones            |                                      |
|---------------------|--------------------------------------|
| FullyQualifiedName  | Nombre de la clase                   |
| DisplayName         | Nombre de la prueba                  |
| Category            | Categoría                            |
| <Trait>             | LLaves y Valores usados en los Trait |


Si se usan atributos [Trait("Llave","Valor")] es posible usar también las combinaciones de llave-valor.

## Seleccionar pruebas en Azure Pipelines

Ejemplo de un pipeline
- https://learn.microsoft.com/en-us/azure/devops/pipelines/ecosystems/dotnet-core?view=azure-devops&tabs=yaml-editor

Usando dotnet

Usando VSTest@3
- https://github.com/microsoft/azure-pipelines-tasks/tree/master/Tasks/VsTestV3


  - task: VSTest@2
    displayName: 'Test Assemblies'
    inputs:
      testAssemblyVer2: |
          $(testAssembliesSearchPattern)
          !**\*TestAdapter*.dll
          !**\*.Testing.dll
          !**\*IntegrationTests*.dll
          !**\*TestFramework*.dll
          !**\obj\**
      vsTestVersion: toolsInstaller
      runInParallel: false
      runTestsInIsolation: true
      codeCoverageEnabled: true
      configuration: '$(buildConfiguration)'


- Ejemplo
- https://github.com/mdabros/SharpLearning.Examples/blob/master/azure-pipelines.yaml

## Publicar resultados en Azure DevOps

- https://docs.specsolutions.eu/specsync/important-concepts/how-to-publish-test-results-from-pipelines-using-the-vstest-task


## Análisis de las pruebas

Test Impact Analysis
- https://learn.microsoft.com/en-us/azure/devops/pipelines/test/test-impact-analysis?view=azure-devops

