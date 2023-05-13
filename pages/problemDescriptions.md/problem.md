# Problem description

A given problem or project requires a description of how its many parts are to
be combined into one or more artifacts.

These descriptions of an external package will be contained in YAML files.

```yaml

# The main `project` dictionary of projects.
# One key per project (one or more projects).
# Each key provides the name of a given project.
projects:

  # The name of a given project (no spaces)
  <aProjectName>:
    # A collection of targets *provided* by this project
    targets:
      # A target type: `libs`, `includes`, ...
      <aTargetType>:
        - <aTargetReleativePath>

    # A list of the tools required by a given worker to build this project
    tools:
      - <firstRequiredTool>
      
    # A collection of dependencies *required* by this project
    dependencies:
      # A dependency type: `packages`, `libs`, `includes`, ...
      <aDependencyType>:
        - <aDependencyRelativePath>
    
    # A list of the actions required to (locally) build this project
    actions: 
        # An action could either be a command line string
        # OR the name of a Python function in the format:
        #     Python:<aModuleName>:<aFunctionName>
        - <firstAction>
```