# JavaScript Work Samples

This repository is contained with some snippets which I generally write in my everyday work:

#1_Task:

The task was to create a screen, where a particular brief information from backend API record has to be shown in a well-defined display along with its relevant meta information in a complex tab-wise subscreen of it. To achieve this requirement, I had to make at least 15+ REST API similar calls in order to get and manipulate the data for meta-information tabular screen set area.

#1_Approached_To_Solve:

As per the respective frontend framework's specified folder structure of the application, there was 1 service file (.js) and multiple UI component files (JS framework component file) for each tabs. So, from general approach in order to get this requirement done, we have to write functions for each API calls for these tabs and include it in service (.js) file. Then importing that service in each UI tab components and use the respective function for that particular component in order to interact with API.

Now all these 15+ API calls are works in a same common pattern but will expect different behaviour/data for each component to work. So, in order to minimize the code lines and make it reusable approach, I wrote a 'JavaScript Closure' and made that service (.js) file as reusable, the same can be used to interact with APIs from each component and also can be used by other co-developers of the application.




```
echo "hello world";

```
