# MonitoringTool_Report

## Day 1:

- SRS document was provided. Mentors explaied about the project and goals that we have to achive in this project.

### Project Goal:

- The goal here is to achieve a tool which can host multiple custom solutions and shows us their live status. This tool will also notify a set of stakeholders, if any of the custom solutions is having a downtime (either partially or fully).
  
- Custom solution: Application/software that are deployed and hosted in the AWS instances.

### Task:

- Two links were given to us. Where we have the hit the end point of an API and to display the status of it.

#### Investigation:

- By using axios as well as fetch in the react app we achived to hit the endpoint of an API and displayed the status of an API.


## Day 2:

### Task: 

- Mentors suggested us to use node.js instead of react.js to achive the hitting API's endpoint and to retrive the status of that API.
- Provided some set of API endpoints where some API endpoints require access token to acess the data.

Investigation: 

```
const express = require('express')
const axios = require('axios');
const app = express()
const port = 5001
app.get('/', (req, res) => {
  res.send('Hello World!')
})
async function checkAPIStatus(apiURL) {
    try {
        const response = await axios.head(apiURL, {
          mode: 'no-cors'
        });
    if (response.status === 200) {
      console.log(`API is reachable. Status: ${response.status}`);
    } else {
      console.log(`API is reachable but returned status code ${response.status}`);
    }
  } catch (error) {
    console.error('Error occurred while trying to reach the API:', error.message);
  }
}
const apiURL = 'https://idp.app-framework.meltwater.io/login';
checkAPIStatus(apiURL);
app.listen(port, () => {
  console.log(`Example app listening on port ${port}`)
})
```

### Issue:

- We faced cors-policy issue while retriving the status of the private API.
- Had some trouble to get the access token of the private API.

 ### Cors-Policy: 
 - Cross-origin resource sharing (CORS) is a browser mechanism which enables controlled access to resources located outside of a given domain.
 - This issue occured because the local host and the provided private API's had different domain.


