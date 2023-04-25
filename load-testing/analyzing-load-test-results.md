# Analyzing Load Test Results

Load tests results display several types of data series over the duration of the test. The data is divided into two graphs:

![](<../.gitbook/assets/image (15) (1).png>)

### Performance Over Time

In the graph the main x-axis is the running time of the test, the y-axis on the left is response time measured in milliseconds, and the right y-axis is the number of active users. On this graph you can track how the number of active users correlates with your application performance using the following metrics:

* **Concurrency** (black) - the number of active users in the test.
* **Avg. Response Time** (green) - the average response time for all successful requests in a given moment in time.
* **50% Response Time** **(purple)** - the 50th percentile for response time, also known as Median. This is the response time value, half of the requests measured below it, and half of the request measured above it.
* **95% Response Time** **(orange)** - the 95th percentile for response time. 5% of the requests measured slower response time than this value.
* **Error rate (red)** - The percentage of failed requests out of the total number of attempted requests for the given moment in time. In case the load test reaches a certain threshold (%50 by default), it will fail.

The difference between average, 50th percentile and 95th percentile, also known as Standard Deviation, can be a useful tool to identify bottlenecks in your applications performance.

### Throughput

This graph represents the number of successful requests per second. As the number of active sessions increases, the number of attempted requests will go higher. When the number of active sessions is constant for some time, changes in throughput will indicate changes in your applications ability to respond fast to requests.
