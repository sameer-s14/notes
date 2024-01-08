## To set up Node.js on your Linux instance

1. Connect to your Linux instance as **ec2-user** using SSH.

2. Install node version manager (nvm) by typing the following at the command line.
``` curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.5/install.sh | bash ```
We will use nvm to install Node.js because nvm can install multiple versions of Node.js and allow you to switch between them.

3. Activate nvm by typing the following at the command line.
    ```. ~/.nvm/nvm.sh```

4. Use nvm to install the latest LTS version of Node.js by typing the following at the command line.
    ```nvm install --lts```

Installing Node.js also installs the Node Package Manager (npm), so you can install additional modules as needed.

5. Test that Node.js is installed and running correctly by typing the following at the command line.
```node -e "console.log('Running Node.js ' + process.version)"```

This displays the following message that shows the version of Node.js that is running.
>Running Node.js VERSION

## Install Ngnix on linux
Ngnix is used for server proxy.
```sudo ap-get install ngnix```

## pm2  
**pm2** is a **Production Process Manager** for Node js applications.
``` sudo npm i -g pm2```
