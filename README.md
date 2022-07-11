# CYOA
CYOA is a choose-your-own-adventure style single page application that runs in your browser. 

## Project setup
Clone this repository to your local machine and install required dependencies
```
gh repo clone dahea/cyoa
npm install
npm install -g json-server
```
json-server [https://github.com/typicode/json-server] creates a mock REST API out of local JSON files 

### Compiles and hot-reloads for development
Run the development server
```
npm run serve
```
In a separate console/terminal window, navigate into the project folder and run the json server 
```
cd ./cyoa
json-server story.json
```
Visit `http://localhost:3000/frames` to view the response.

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

