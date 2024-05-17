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

**Client Side Errors**
- 400 Bad Request.
- 401 Unauthorized.
- 402 Payment Required.
- 403 Forbidden.
- 404 Not Found.
- 405 Method Not Allowed.
- 408 Request Timeout.
- 409 Conflict

**Informational**
- 413 Payload too large.
- 415 Unsupported Media Type.
- 422 Unprocessable Entity.
- 429 Too many request.
- 451 Unavailable for legal reasons.
- 500 Internal server error.
- 503 Service Unavailable
- 504 Gateway Timeout

**Redirectional**
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

