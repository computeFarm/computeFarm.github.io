# Descriptions of external packages

A given problem or project may depend upon a number of external packages.

These external packages my either be already installed, or might be downloaded,
compile and (locally) installed as part of the process of building a project.

A description is required for each external package.  These descriptions of an
external package will be contained in YAML files.

```yaml
# The main `packages` dictionary of external packages.
# One key per package (one or more packages).
# Each key provides the name of a given package.
packages:

  # The name of a given package (no spaces).
  <aPackageName>:
    # A description of how to obtain this package
    repoProvider: <github|http|local|apt|...>
    repoPath: <aUrl>
    version: <aVersionNumber>

    # A collection of targets *provided* by this package
    targets:
      # A target type: `libs`, `includes`, ...
      <aTargetType>:
        - <aTargetReleativePath>

    # A collection of dependencies *required* by this package
    dependencies:
      # A dependency type: `packages`, `libs`, `includes`, ...
      <aDependencyType>:
        - <aDependencyRelativePath>
    
    # A list of the tools required by a given worker to install this package
    tools:
      - <firstRequiredTool>
      
    # A list of the actions required to (locally) install this package
    actions: 
        # An action could either be a command line string
        # OR the name of a Python function in the format:
        #     Python:<aModuleName>:<aFunctionName>
        - <firstAction>
```

----

**NOTE** : to dynamically map a string to a Python function in a given module
see:

- https://stackoverflow.com/questions/4018953/whats-the-way-to-call-a-function-dynamically-in-python and 

- https://docs.python.org/3/library/importlib.html




