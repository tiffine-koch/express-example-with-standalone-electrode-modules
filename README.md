# Express App with Electrode Modules
- This repo is a sample Express app generated from `express app` with Electrode modules
- You can clone the repo and `npm install` + `NODE_ENV=development npm start` or follow along with the instructions to build it from scratch

## Express generator
- Scaffold an express app: 

```
npm install express-generator -g
express app
cd app 
npm install 
```

## Electrode Confippet
- Confippet is a standalone module that can be used w/o other parts of electrode

```
npm install electrode-confippet --save
```

### Config Files
- Create the config folder: 

```
mkdir config
cd config
```

- Add the following config files: 

```
config
|_ default.json
|_ development.json
|_ production.json
```

- Add your configuration settings 
- Update the `config/default.json` to have the following settings: 

```
{
  "server": {
    "viewCache": false,
    "xPoweredBy": true,
    "port": 4000
  }
}
```

### Development Environment
- Update the `config/development.json` to have the following settings: 

```
{
  "server": {
    "viewCache": false,
    "xPoweredBy": true,
    "port": 4000
  }
}
```

- The above settings disable view cache, enable x-powered-by header and run the server in port 4000

### Production Environment
- Update the `config/production.json` to have the following settings: 

```
{
  "server": {
    "viewCache": true,
    "xPoweredBy": false,
    "port": 8000
  }
}
```

- The above settings enable view cache, disable x-powered-by header and run the server in port 8000
- Keys that exist in the `config/default.json` that are also in the other environment configs will be replaced by the environment specific versions

### Confippet Require
- Add the following to app.js: 

```
const config = require("electrode-confippet").config;

app.set("view cache", config.server.viewCache);
app.set("x-powered-by", config.server.xPoweredBy);
app.listen(config.server.port);
```

### Running Electrode app
- Start the express app in `development` environment: 

```
NODE_ENV=development npm start
```

- Start the express app in `production` environment: 

```
NODE_ENV=production npm start
```

- Running in the selected environment should load the appropriate configuration settings
