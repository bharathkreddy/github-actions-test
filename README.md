# Github actions
***
## 1. Structure of YAML ✨
- yml or yaml : **Both mean the same thing**
- Similar to json, yaml is **key value pairs**
- Examples
    ```yaml
    name: bharath            //no quotations for Strings//
    age: 23                  //space after the colon//
    address: "47:uplands"    //quotations if string has colons//
    current: true            //boolean values//
    key:                     //can have arbiatry levels//
        key1: value1
        key2: value2
        key3:
            sub_key: sub_value
    array:                  //arrays each object starts with hypen and indented//
        - item1
        - item2
        - {key: value}
    object_array:            //each object in array has 2 keys//
        - key1: value1
          key2: value2
        - keya: valuea
          keyb: valueb
    long_text: >             // same as  "long_text": "fdas fda fd adf  fdasfa  fdabc\n" //
        fdas fda fd adf 
        fdasfa 
        fdabc
    preserve_space: |        //same as "long_text": "fdas fda fd adf \nfdasfa \nfdabc\n" //
        fdas fda fd adf 
        fdasfa 
        fdabc
    ```

## 2. Github Actions YAML Structure
***
1. **name** : The name of your workflow. GitHub displays the names of your workflows on your repository's actions page. If you omit this field, GitHub sets the name to the workflow's filename.

2. **on**: The name of the GitHub event that triggers the workflow. You can provide a single event string
    ```yaml
    on: push
    ```
    or array of events, array of event types,
    ```yaml
    on: [push,public]  #public: when repo goes from private to public
    ~~~~~~~~~~~~~~~
    on:
      pull_request:
        types: [opened, reopened]
    ```
     or an event configuration map that schedules a workflow or restricts the execution of a workflow to specific files, tags, or branch changes. 
     ```yaml
     on:
       schedule:
        - cron: "* * 1 1-6 *" #https://crontab.guru/  
        - cron: "0 22 * * MON-FRI"   #multiple cron jobs 
    ~~~~~~~~~~~~~~~~~~
    on:
      repository_dispatch:    # uses a webhook, called repositary_dispatch, an external post request is needed to trigger this. 
        types: [lock]  # send post request to url with this event_type as body of post. This request can have a payload too which can be read.
     ```
     ![postman1](/Users/bharathreddy/Desktop/github_token.png "github token")
     ![postman1](/Users/bharathreddy/Desktop/postman_token.png "postman token")
     ![postman1](/Users/bharathreddy/Desktop/github_header.png "postman header")
     ![postman1](/Users/bharathreddy/Desktop/github_body.png "postman body")


3. **jobs**: A workflow can have one or more jobs. Each job runs on a seperate VMs and run parallelly but can also run in a serial. 

  **name-of-the-job**:

    **runs-on**:Operating system of the runner. 

    **needs**:[array of "name-of-the-job" in quotes, of job on which this jobs depends, or job IDs]

    **steps**: this is an array of objects, each step can perfrom an action or run a command.

      **- name**: name of the step

       **run**: the command to run, can be single or multi lined or mention a specific shell to run the command.

```yaml
run : echo "hello world"
~~~~~~~~~~~~~~~~~~~~~~~~
run: |     # pipe allows multi line 
    echo pwd
    npm -v
~~~~~~~~~~~~~~~~~~~~~~~~~
run: |
    import random
    for x in range(1,10):
    print(random.randint(0,9)) 
shell: python 
```

**jobs**:

  **name-of-the-job**:

    **runs-on**:

    **needs**:

    **steps**: 

      **- name**: 

       **uses**: instead of run to execute a command, uses refers to an action. Actions can be written and referenced as a path or can be used directly if published in some other git hub repo. If this is other repo then format is {username}/{repo name}@{version} or instead of version we can also metion a specific commit id.

        **- with**:

          **{input}:** this is key value pair of inputs for any action specified in the uses part.

```yaml
jobs:
  run-github-actions:
    runs-on: ubuntu-latest
    steps:
      - name: Simple Java Script Action
        id: greet   # optional ID for each step, but needed if a step has to be referenced somewhere.
        uses: actions/hello-world-javascript-action@v1.1   #this is a published action on a github repo
        with:
          who-to-greet: 'BRK the UberCoder'   #on github rep called actions/hello-world-javascript-action, the documentation gives inputs needed for this action.
    - name: Log Greeting Time   #actions can also generate output, here we have created a new step to capture this output.
        run: echo "${{ steps.greet.outputs.time }}" # in order to reference a step we need its ID, see above.   
```




## 3. First Workflow✨
***
1. All workflows should be in **.gihub/workflows/** folder
2. Here is the first simple file called [**simple.yml**](.github/workflows/simple.yml)
3. Here is the first actions file called [**actions.yml**](.github/workflows/actions.yml)
4. 

## 3. 