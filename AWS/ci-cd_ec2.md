# Aws EC2
Amazon Elastic Compute Cloud (Amazon EC2) provides on-demand, scalable computing capacity in the Amazon Web Services (AWS) Cloud. Using Amazon EC2 reduces hardware costs so you can develop and deploy applications faster.
You can use Amazon EC2 to launch as many or as few virtual servers as you need, configure security and networking, and manage storage.
You can add capacity (scale up) to handle compute-heavy tasks, such as monthly or yearly processes, or spikes in website traffic.
When usage decreases, you can reduce capacity (scale down) again.

## Steps To Setup Repository with ec2 and github actions: 

**AWS Console Steps**

Select Launch EC2 instance from aws console from EC2 section.
1. Provide Name to instance.
2. Choose operating system
3. Configure Your Machine sytems
4. Create a key pair login
        type - RSA
        file format - pem --> Mac,Linux user
                    - ppk --> Windows user
 - This File is used to connect to our aws instance termial from our local machine.  
5. You can Launch the instance with default configuration or change it accordingly.

***For Connecting with instance Terminal***
1. Select the instance 
2. Then Select Connect from Actions.
3. Select the options by Which you want to connect with instance.
    There are 4 options.
    - a. To connect you local machine with instance select ***ssh client*** 
        - Follow the instructions provided there in a directory where pem file is present.
    - b. Select ***EC2 instance connect*** to connect with instance using aws console only.
    


>Also Set inbound rules in Security Group Section , Used by the particular Instance.To make a http connection with instance.
1. By Default it provides SSH Rule.
2. Select Edit inboud rule after that add another new roule 
        Type -> Http > as we will be using this for our apis
        Port range -> Our Project Port > The default port is 80 and it does not need to mention on api route also because it was default for all servers.
        Source -> Anywhere-IPv4 0.0.0.0/0 

**Github Steps**
1. Go to you github Repository
2. Settings -> Actions -> Runners -> New Self-hosted runner (if you want to create a new runner)
3. Select the OS accordin to your instance (In our case Linux).
4. Follow commands and instruction provided there on our ***EC2 terminal***.
    - There are two section 
    a. ***Download*** - To Download the required files in a seperate directory .
    b. ***Configure*** - To configure the files to implement runners on our server.

> After All these Steps Again Go to Settings -> Actions -> Runners You will see the server ip there but it will be in offline status.

* To Start the this runner - 
a. Go To ***Terminal*** in the folder created in ***4th step*** in ***Download section*** in our case it is auction-runner.
b. Run these commands 
    ```
    sudo ./svc.sh install  # This file is downloaded or extracted during download process in step 4 of github actions
    sudo ./svc.sh start # This will start our runner in Background.And change the status to idle
    ```

To set Env variables 
1. Go to Settings -> Secrets and Variables -> Actions -> Create New Env Secret
2. There Give File name and all the variables used in project.


**CI/CD workflow**
1. Select ***Actions Tab***, present on top of selected repository page.
2. For Node Project, Go to ***Nodejs*** in ***Continuous integration*** and Click Configure.
3. This will open the [Your Project]/.github/workflows/node.js.yml file
4. Change accordingly
5. Make changes in trigger
6. File contains certain steps for implementation of runner. and task perform when trigger is trigered.
example: 
```
name: Node.js CI

on:
  push:
    branches: [ "main" ]   // Can change to branch which you want to target.
    // Removed pull_request trigger.

jobs:
  build:
    runs-on: self-hosted  //Changed to self-hosted.

    strategy:
      matrix:
        node-version: [ 18.x] // Changed to select only latest version
 steps:
    - uses: actions/checkout@v3
    - name: Use Node.js ${{ matrix.node-version }}
      uses: actions/setup-node@v3
      with:
        node-version: ${{ matrix.node-version }}
        cache: 'npm'
    - run: npm ci   // run clean install to remove old node_modules
    - run: |        // pipe is used to run multiple commands
      touch .env    // Creating env file
      echo "${{sceret.[file name]}}" > .env   // File name is the file created in ***Github  steps section, while setting env file*** to echo it in .env file
```

* After that commit the changes and now,
* You can view the details of action runner workflow in **Actions Tab** And the process it is taking for implementation for CI/CD.
* You can check on server also inside the [action runner]/_work folder there will be a dir named with your repository.


## Configuring the Ngnix with proxy information.

change dir to ***etc/ngnix/sites-available***
This directory conains file called ***default*** which we need to change 
command to make write changes is ***sudo nano default***

In this file make these changes 

**write after location / {}**

```
location /api {
  rewrite ^\/api\/(.*)$1 break;
  proxy_pass http://localhost:5000; // To redirect the url to this.
  proxy_set_header HOST $host;
  proxy_set_header X-Real-IP $remote_addr;
  proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
}
```

**After making any changes in Ngnix confihuration restart the ngnix server**
>sudo systemctl restart ngnix

## Start Server

1. Go to the project directory in **actions folder/_work/git repo name**
2. Start server
    > pm2 start server.js --name-[process name(any name for the process)]

