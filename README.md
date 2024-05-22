# Monitoring Tool Report

## Day 1:

- **Activity:** 
  - Received SRS document and project briefing from mentors.
  - Discussed project goals: Developing a tool to host multiple custom solutions and display their live status. Tool to notify stakeholders in case of downtime.
  - Defined custom solution as applications/software hosted on AWS instances.
    
- **Task:**
  - Provided with API endpoints to hit and display their status.
 
- **Progress:**
  - Successfully implemented API endpoint hitting and status display using Axios and Fetch in React app and testing it by making a GET request in Postman.

## Day 2:

- **Task:** 
  - Mentors suggested using Node.js instead of React.js for API endpoint handling.
  - Provided API endpoints, some requiring access tokens which threw a status 401 Unauthorised error.
 
- **Progress:**

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
### Status Codes:
**Success Code Series:**
- 200 OK: Successful request.
- 202: Accepted.
- 203 Non-Authoritative Information.
- 204: No Content.
- 205: Reset Content.
- 206: Partial Content.

**Client Side Errors:**
- 400 Bad Request.
- 401 Unauthorized.
- 402 Payment Required.
- 403 Forbidden.
- 404 Not Found.
- 405 Method Not Allowed.
- 408 Request Timeout.
- 409 Conflict

**Informational:**
- 413 Payload too large.
- 415 Unsupported Media Type.
- 422 Unprocessable Entity.
- 429 Too many request.
- 451 Unavailable for legal reasons.
- 500 Internal server error.
- 503 Service Unavailable
- 504 Gateway Timeout

**Redirectional:**
- 301 Moved Permanently.
- 302 Found but moved temporarily.
- 304 Not modified.

### Issue:

- We faced cors-policy issue while retriving the status of the private API.
- Had some trouble to fetch the access token of the private API.

 ### Cors-Policy: 
 - Cross-origin resource sharing (CORS) is a browser mechanism which enables controlled access to resources located outside of a given domain.
 - This issue occured because the local host and the provided private API's had different domain.

## Day 3:

### Task:
- To fetch the access token from the network tab through code.
- To schedule it to get renewed before 24 hours since the token expires.

**Progress:**
- Were able to fetch the token manually by inspecting the network tab of the page.
- Could hit the endpoint by including the token in the headers authorisation.

## Day 4:

### Task:
- To fetch the access token from the network tab through code by using puppeeter.
- To perform code level monitoring for the provided custom solution.

**Progress:**
- We investigated some approaches to fetch access token from the network tab, out of which we decided to use puppeeter. 
- For scheduling the renewal of token we used cron job schedulling approach.

**Puppeeter**
- Puppeteer is a Node.js library that provides a high-level API for controlling and automating web browsers.
- It supports a wide range of browser automation features, including navigating pages, interaction with elements, filling forms, clicking buttons 
  and handling events.
- Allows you to take screenshots of web pages, capture PDFs and even generate videos of the rendered pages, making it useful for visual testing and 
  monitoring.
- It provides powerful tools for debugging and troubleshooting, includes the ability to trace network request, intercept responses and emulate 
  various devices and network condition.
- Can be integrated with popular testing framework like *Jest* or *Mocha*, making it valuable tool for end to rnd testing.

**Cron Job Schedular**
- Cron jobs are scheduled at recurring intervals, specified using a format based on unix-cron. You can define a schedule so that your job runs 
  multiple times a day, or runs on specific days and months.
- A schedule is defined using the unix-cron string format (* * * * *) which is a set of five fields in a line, indicating when the job should be 
  executed.
  ![cron job](https://github.com/karthik30018/MonitoringTool_Report/assets/143400284/d8738751-5a99-415b-9477-e42ffc9137b4)
- To play around with it, reffered this link - https://crontab.guru/.## Day 4:

## Day 5:

### Task:
- Using Ngrok to Host: We talked about using Ngrok to host our application. It’s a tool that helps us share our local server with others over the internet. This can be handy for testing and 
  showing our work to others.

**Progress:**
- We have implemented the retrieval of the authorisation token using puppeteer headless browsing and by specifying the username and password.
- The next steps include encrypting sensitive data using .env files and automating the fetching of the authorisation token using cron job.

**NgRok**

- A tool that provides a secure tunneling to your local development environment or server.
- Basically it allows you to expose your local server behind your local internet or firewall to the outside internet, which makes it easier and accessible for testing or debugging.

## Day 6:

### Task:
- Encryping the sensitive data.
- To create seperate server for healthCheck(EndPointCheck).

**Progress:**
- We also hosted the script on ngrok, where it could be accessible by the team members via the link.

## Day 7:

### Task:
- Provided a custom solution for which we were required to perform error handling for code level checking.

**Progress:**
- Stored all the sensitive data inside the `.env` file.
- Created a seperate server script for the healthCheck.

## Day 8:

### Task:
- To implement batch scheduling for the APIs, allowing them to be called simultaneously.
- To check for the status codes other than 200,400 and 500 in the same series.

**Progress:**
- Implemented error mechanism to the provided custom solution and created a seperate middleware to display the code runtime error messages.
  
    

