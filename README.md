
![3/cover.png](http://logo.apimacro.com/3/cover.png)

# [www.apimacro.com](https://www.apimacro.com/)

+ [www.apimacro.com](https://www.apimacro.com/)
+ [logo.apimacro.com](https://logo.apimacro.com/)
+ [docs.apimacro.com](https://examples.apimacro.com/)
+ [bash.apimacro.com](https://bash.apimacro.com/)
+ [examples.apimacro.com](https://examples.apimacro.com/)


## DEFINITIONS

An API (Application Programming Interface) is a set of rules and protocols for building and interacting with software applications. It specifies how software components should interact and allows different software systems to communicate with each other.

A Macro, in computer science, usually refers to a rule or pattern that specifies how certain input sequences should be mapped to output sequences according to a defined procedure. 

"API Macro" referring to a predefined set of API calls or instructions

## DESCRIPTIONS

"API Macro" is used to define a script in YAML that orchestrates the behavior of multiple APIs and services.

In essence, this file seems to define a sequence of operations (or a "macro") for connecting to various services, each of which has its own adapter written in a different language (Python, NodeJS, Java, and so on). So, this "API Macro" acts as a configuration or a script that ties these separate operations together to accomplish more complex tasks -- such as logging in to a site and taking a screenshot.

## Benefits:

### Flexible and Language-agnostic
As the "API Macro" defines a high-level sequence of operations, it allows these operations to be carried out in multiple programming languages.

### Reusability and Modularity
Independent parts (like taking a screenshot, or logging in) might be swapped out or re-used in different sequences. This can lead to more maintainable and understandable code.

### Streamlined Workflow
By articulating the process in this declarative way, it can be easily read and understood. This allows for clarity in defining workflows, and simplifies the process of executing complex operations.



## DSL (Domain Specific Language) solutions

This "API Macro" approach is domain-specific language, as it defines its "commands" (like "SCREENSHOT", "FOCUS", etc.). 
A DSL is a computer language specialized to a specific application domain, and in this case, the DSL is used for managing and orchestrating various API interactions.

anopther solutions:

- **MakeFile**: Used mostly in C and C++ development, a MakeFile specifies a set of directives about how to compile and link a program.
- **Docker-Compose**: A tool for defining and managing multi-container Docker applications. Configuration is done in a YAML file where services, networks, and volumes are defined.
- **Kubernetes Manifests**: Kubernetes uses a similar approach but on a larger/more complex scale where YAML files are used to define the architecture and communication of containers over a cluster of machines.
- **Bash scripting**: Bash or shell scripting is another similar solution. A bash script can be written to execute commands in order, from different programming languages, or even execute programs or APIs.


Remember though that while providing the flexibility of using different languages and easy process management, such YAML "API Macro" requires properly maintained and up-to-date documentation to be used effectively due to its customized nature.




## Example

API macro is providing configuration in yaml to define the connection between libraries, adapters in many languages and use such configuration for environment in yaml config file:

```yaml
INIT: "git@github.com:apirpc/apirpc.git"
    
IMPORT:    
    XPATH:
        SOURCE: "git@github.com:apirpc/list.git"        
        ADAPTER: "python/xpath.py"
        DOCKER: "python/DOCKERFILE"
    TXT_FROM_FILE_PATH:
        GIT: "git@github.com:apirpc/txt_from_file_path.git"
        ADAPTER: "nodejs/txt_from_file_path.nodejs"
        DOCKER: "nodejs/DOCKERFILE"
    BROWSER:
        GIT: "git@github.com:apirpc/browser.git"
        ADAPTER: "java/browser.java"
        DOCKER: "java/DOCKERFILE"
    SCREENSHOT:
        GIT: "git@github.com:apirpc/puppetter.git"
        ADAPTER: "js/browser.js"
        DOCKER: "js/DOCKERFILE"
            
SET:
    URL: https://strato.pl/auth/login.html
    PATH_OUT: "/screenshots/"    
    PATH_IN: "/provider/"
    FOLDER_PROVIDER: "strato.pl"
    PATH_USER:
        - "file://"
        - FOLDER_PROVIDER
        - "/.user"
    PATH_PASS:
        - "file://"
        - FOLDER_PROVIDER
        - "/.pass"
```

the api macro is defined as a yaml code:
```yaml
BROWSER:
    GET: URL
    FOCUS:
        XPATH: "input.text.login"
    WRITE:
        TXT_FROM_FILE_PATH: PATH_USER
    FOCUS:
        XPATH: "input.text.password"
    WRITE:
        TXT_FROM_FILE_PATH: PATH_PASS
    WAIT: 3000
    CLICK:
        XPATH: "input.mid.button-green-large"
    SCREENSHOT:
        - MIMETYPE: FILE_FORMAT
        - GET: URL
        - SIZE: HD
        - PATH:
            - FOLDER: PATH_SCREENSHOT
            - FILE_NAME:
                HOST_NAME: URL
```
the example is going to URL page and is trynig to login and creating a SCREENSHOT






---

Macro builder based on CSV data format and Command with bash scripts


---

+ [edit](https://github.com/apimacro/www/edit/main/README.md)
+ [apimacro/logo/](https://github.com/apimacro/www/)
