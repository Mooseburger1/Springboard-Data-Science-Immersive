This is a SQL case study as proposed from Mode Analytics at https://modeanalytics.com/.
The Jupyter notebook in this repository is a cleaned up verison of the original case study which contains all original SQL queries, and can be found here:
https://modeanalytics.com/mooseburger/reports/14cbbb5670b8

Yammer’s Analysts are responsible for triaging product and business problems as they come up. In many cases, these problems surface through key metric dashboards that execs and managers check daily.

## The problem
You show up to work Tuesday morning, September 2, 2014. The head of the Product team walks over to your desk and asks you what you think about the latest activity on the user engagement dashboards. You fire them up, and something immediately jumps out:
![alt text](https://github.com/Mooseburger1/Springboard-Data-Science-Immersive/blob/master/SQL/Yammer%20Case%20Study/Yammers.png)

The above chart shows the number of engaged users each week. Yammer defines engagement as having made some type of server call by interacting with the product (shown in the data as events of type “engagement”). Any point in this chart can be interpreted as “the number of users who logged at least one engagement event during the week starting on that date.”

You are responsible for determining what caused the dip at the end of the chart shown above and, if appropriate, recommending solutions for the problem.


## Results
![alt text](https://github.com/Mooseburger1/Springboard-Data-Science-Immersive/blob/master/SQL/Yammer%20Case%20Study/result.png)
The drop off in active users appears to be correlated with phone users. In the image above, it can be seen there is a substantial drop off in active phone users around the same time frame as the drop in overall active users count. There was a drop off in computer users as well, but not to the magnitude of phone users. And the Computer users did see a recovery where phone users did not. 
