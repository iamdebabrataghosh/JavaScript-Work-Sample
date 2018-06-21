# JavaScript Work Samples

This repository is contained with some snippets which I generally write in my everyday work:

#1_Task:

The task was to create a screen, where a particular brief information from backend API record has to be shown in a well-defined display along with its relevant meta information in a complex tab-wise subscreen of it. To achieve this requirement, I had to make at least 15+ REST API similar calls in order to get and manipulate the data for meta-information tabular screen set area.

#1_Approached_To_Solve:

As per the respective frontend framework's specified folder structure of the application, there was 1 service file (.js) and multiple UI component files (JS framework component file) for each tabs. So, from general approach in order to get this requirement done, we have to write functions for each API calls for these tabs and include it in service (.js) file. Then importing that service in each UI tab components and use the respective function for that particular component in order to interact with API.

Now all these 15+ API calls are works in a same common pattern but will expect different behaviour/data for each component to work. So, in order to minimize the code lines and make it reusable approach, I wrote a 'JavaScript Closure' and made that service (.js) file as reusable, the same can be used to interact with APIs from each component and also can be used by other co-developers of the application.

```javascript
// 'A JavaScript Closure' to automate same/similar API calls of the application. (#Included it in service (.js) file)
processRequest(http, id, apiEndPoint, method, data) {
    var urlEndPoint = apiEndPoint; // API endpoint, which needed to be specified from the tab component
    var baseUrl = 'https://example.com/api/v2';
    function apiRequest() {
      function getCall() {
        return http.get(`${baseUrl}/${urlEndPoint}/${id}`).then((response) => {
          return response.data;
        }, (error) => { // eslint-disable-line
          return error;
        }).catch((exception) => { // eslint-disable-line
          // Handle exception here
        });
      }
      function postCall() {
        return http.post(`${baseUrl}/${urlEndPoint}/${id}`, data).then((response) => {
          return response.data;
        }, (error) => { // eslint-disable-line
          return error;
        }).catch((exception) => { // eslint-disable-line
          // Handle exception here
        });
      }
      /** Similarly we can also add more HTTP methods (like PUT, DELETE etc.) to support this closure */
      if (method === 'get' && typeof data === 'undefined') {
        return getCall();
      } else if (method === 'post' && typeof data !== 'undefined') {
        return postCall();
      }
    }
    return apiRequest();
  }

```
