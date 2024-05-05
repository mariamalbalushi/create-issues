# create-issues
 

This is a very small project intended to facilitate issue creation on GitHub. Give it a CSV file and it will bulk create those issues.

## Running Locally

###### Make sure you have [Node.js](http://nodejs.org/) installed.

```sh
https://nodejs.org/en/
```

###### Create a tab separated data.csv file (or modify the existing one) in the root directory, like the following:

```
title  
Issue-1 
Issue-2 
```

###### Note that you can give it multiple assignees:

```
title   
Issue-3
```

###### Create an access token from GitHub
```$xslt
https://docs.github.com/en/github/authenticating-to-github/creating-a-personal-access-token
```

###### Get that token and put it in **.env** file in the root of your project:

In .env.example file, you'll also have to specify the remaining fields: OWNER, REPO and FILENAME. Don't forget to change .env.example to .env.

```$xslt
TOKEN=(token)
OWNER=(owner name)
REPO=test
FILENAME=data.csv
```

###### The default delimiter (separator) is the tab character (\t). 
You may change this from the code in **createIssues.js**
```
module.exports = (filename, data) => {
    fs.createReadStream(filename)
        .pipe(csv({separator:'\t'}))
        .on('data', async (row) => {
```

###### Now you have your project ready to run:

```$xslt
npm install
node index.js
```

Wait for a while, and you'll find your issues created in your specified repository.

