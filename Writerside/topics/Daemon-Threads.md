# Daemon Threads

Daemon threads play a key role in executing background tasks that support the main application.<br />
These threads do not keep the JVM alive; the JVM will exit when all user threads finish, even if daemon threads are still running.<br />
Daemon threads are designed to perform low-priority tasks.


### Key Characteristics

- <b>Background Execution:</b> They run in the background, performing tasks such as clean up, monitoring, or support services.
- <b>Lifecycle:</b> The JVM does not wait for daemon threads to complete before shutting down. If only daemon threads remain, the JVM automatically exits.
- <b>Low Priority:</b> They are generally assigned lower priority than user threads.
- <b>Auxiliary Tasks:</b> Used for non-critical tasks like garbage collection, caching, or logging.


### Daemon vs User Threads
| Aspect          | Daemon Threads                          | User Threads                          |
|-----------------|-----------------------------------------|---------------------------------------|
| Keeps JVM Alive | No                                      | Yes                                   |
| Termination     | JVM terminates when user threads exit   | Must complete or explicitly terminate |
| Priority        | Lower                                   | Higher                                |
| Use Case        | Garbage collection, logging, monitoring | Business logic, user interactions     |

### Setting a Thread as Daemon
Mark a thread using the `setDaemon(true)` method. This must be done before starting the thread, as changing its daemon status after starting will throw an ``IllegalThreadStateException.

```java
public class DaemonThreadExample {
    public static void main(String[] args) {
        // Create a new thread
        Thread daemonThread = new Thread(() -> {
            while (true) {
                System.out.println("Daemon thread is running...");
                try {
                    Thread.sleep(1000);
                } catch (InterruptedException e) {
                    System.out.println("Daemon thread interrupted.");
                }
            }
        });

        // Set the thread as a daemon thread
        daemonThread.setDaemon(true);

        // Start the daemon thread
        daemonThread.start();

        // Main thread does some work
        System.out.println("Main thread is working...");
        try {
            Thread.sleep(3000);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }

        System.out.println("Main thread is done. Exiting...");
    }
}
```
### Lifecycle of Daemon Threads
Daemon threads are inherently tied to the lifecycle of the JVM. Here's how their lifecycle works:

   1. A daemon thread starts and runs concurrently with other threads.
   2. If all user threads finish, the JVM terminates, and any running daemon threads are stopped abruptly.
   3. If a thread is created by a daemon thread, it is also a daemon thread.

### Categories of Tasks Suitable for Daemon Threads
1. **System Monitoring and Diagnostics**
   - Monitoring CPU temperature.
   - Tracking disk I/O usage.
   - Measuring memory usage trends.
   - Monitoring thread pool activity.
   - Collecting JVM heap statistics.
   - Logging error rates over time.
   - Sending real-time application health updates.
   - Monitoring database query performance.
   - Aggregating server response times.
   - Tracking API call latencies.
   - Monitoring system-wide process activity.
   - Recording system uptime statistics.
   - Detecting deadlocks in threads.
   - Monitoring event loop lags.
   - Capturing stack traces periodically for analysis.
   - Tracking container resource usage in Kubernetes.
   - Monitoring network bandwidth usage.
   - Checking for unresponsive threads.
   - Recording the number of active database connections.
   - Monitoring application startup times.
2. **Logging and Analytics**
   - Writing debug information to files.
   - Syncing logs to external log aggregation systems (e.g., ELK stack, Splunk).
   - Collecting application usage statistics.
   - Tracking request-response pairs for debugging.
   - Logging user interactions for analytics.
   - Recording API usage metrics.
   - Capturing remote error logs from client devices.
   - Aggregating logs from distributed microservices.
   - Logging non-critical warnings or notices.
   - Tracking message queue processing rates.
   - Writing system event summaries periodically.
   - Logging successful or failed database queries.
   - Tracking external API response codes.
   - Recording cache hits and misses.
   - Logging function execution times.
   - Capturing runtime exceptions and stack traces.
   - Writing HTTP access logs.
   - Recording background job execution metrics.
   - Aggregating logs from multiple application nodes.
   - Syncing logs to a remote storage bucket.
3. **Background Maintenance**
   - Cleaning up unused files in temporary directories.
   - Deleting expired cache entries.
   - Compacting log files.
   - Rotating system logs to avoid disk overuse.
   - Pruning old data from in-memory structures.
   - Rebalancing load across distributed caches.
   - Rebuilding corrupted index files.
   - Cleaning up old database snapshots.
   - Resetting stale database connections.
   - Refreshing system configuration.
   - Cleaning up abandoned user sessions.
   - Optimizing database query plans.
   - Compacting fragmented database tables.
   - Cleaning orphaned files after incomplete uploads.
   - Removing unused Docker containers and images.
   - Updating in-memory indexes periodically.
   - Clearing expired security tokens.
   - Cleaning up redundant files in distributed storage.
   - Removing unused application artefacts.
   - Purging stale analytics data.
4. **Cache Management**
   - Evicting expired cache entries.
   - Preloading frequently accessed data.
   - Updating distributed cache consistency.
   - Refreshing in-memory cache values.
   - Removing stale cache keys.
   - Rebuilding cache indices.
   - Monitoring cache hit/miss rates.
   - Cleaning up unused cache segments.
   - Compacting cache storage.
   - Tracking cache usage over time.
   - Synchronizing distributed cache nodes.
   - Auto-scaling distributed cache shards.
   - Clearing outdated cache entries after deployments.
   - Generating cache warming data asynchronously.
   - Monitoring cache memory usage.
   - Evicting least recently used (LRU) cache entries.
   - Periodically validating cache integrity.
   - Cleaning up dangling references in cache systems.
   - Refreshing invalidated cache data.
   - Rebuilding in-memory cache maps.
5. **Network Operations**
   - Monitoring network latency for microservices.
   - Polling external APIs for updates.
   - Performing DNS lookups for backend services.
   - Testing connectivity to external services.
   - Monitoring active TCP/IP connections.
   - Tracking network packet loss rates.
   - Logging API call retries for failed requests.
   - Performing health checks for downstream services.
   - Monitoring HTTP request/response latencies.
   - Updating network configuration dynamically.
   - Logging SSL/TLS handshake performance metrics.
   - Monitoring socket connection pools.
   - Detecting failed network connections.
   - Tracking DNS resolution performance.
   - Monitoring web server thread health.
   - Updating load balancers asynchronously.
   - Logging network throughput statistics.
   - Monitoring VPN connection stability.
   - Recording failed outgoing API calls.
   - Tracking real-time outbound network traffic.
6. **Data Aggregation and Processing**
   - Streaming logs into a centralised log system.
   - Aggregating telemetry data from IoT devices.
   - Preprocessing analytics data for dashboards.
   - Periodically updating report summaries.
   - Aggregating usage metrics from multiple endpoints.
   - Collecting system-wide latency statistics.
   - Building derived metrics from raw telemetry data.
   - Generating statistical summaries of API usage.
   - Collecting user behaviour data for analysis.
   - Assembling datasets for machine learning pipelines.
   - Aggregating error rates across services.
   - Collating analytics data from distributed nodes.
   - Generating time-series metrics from raw logs.
   - Periodically compressing old telemetry data.
   - Collecting event logs for anomaly detection.
   - Cleaning up duplicate entries in data streams.
   - Aggregating low-priority business events.
   - Preloading analytics data into dashboards.
   - Tracking aggregated user activity statistics.
7. **Resource Management**
   - Cleaning up abandoned resources in cloud environments.
   - Terminating idle virtual machines.
   - Monitoring container CPU and memory usage.
   - Cleaning up expired API keys.
   - Rotating encryption keys periodically.
   - Ensuring resource limits are not exceeded.
   - Tracking resource allocation trends.
   - Monitoring storage utilisation thresholds.
   - Reclaiming unused system memory.
   - Cleaning up unused IAM roles or permissions.
   - Compacting fragmented storage volumes.
   - Monitoring disk usage across distributed systems.
   - Resetting resource quotas periodically.
   - Logging resource usage spikes.
   - Monitoring Kubernetes pod resource metrics.
   - Recording unused resources for future cleanup.
   - Cleaning up unused cloud storage buckets.
   - Monitoring ephemeral storage consumption.
   - Terminating unused background jobs.
   - Rotating cloud access credentials.
8. **UI and User Support**
   - Preloading non-essential UI assets (e.g. images, videos).
   - Generating suggestions for autocomplete fields.
   - Updating in-memory user activity heatmaps.
   - Cleaning up old user preferences asynchronously.
   - Preloading user-specific recommendations.
   - Tracking user session activity in the background.
   - Recording non-critical user error messages.
   - Generating personalised user tips in real-time.
   - Monitoring user activity to detect inactivity.
   - Preloading localisation assets for user interfaces.
   - Fetching non-critical data for user dashboards.
   - Updating user-specific analytics asynchronously.
   - Preloading non-essential content for faster page loads.
   - Tracking time spent on specific user actions.
   - Monitoring user interaction patterns in real-time.
   - Preloading low-priority user assets for caching.
   - Syncing UI state for offline users.
   - Fetching non-critical notifications for users.
   - Recording user interface performance metrics.
9. **Asynchronous Event Handling**
   - Handling low-priority webhook events asynchronously.
   - Processing delayed email notifications.
   - Handling retry events for failed API calls.
   - Cleaning up abandoned event queue messages.
   - Processing low-priority user-generated events.
   - Handling non-critical alerts from monitoring systems.
   - Aggregating system-wide event logs.
   - Cleaning up expired scheduled events.
   - Polling external webhook systems for updates.
   - Retrying failed notifications to user devices.
   - Processing delayed push notifications.
   - Polling for low-priority events in message queues.
   - Cleaning up unused event subscriptions.
   - Monitoring event delivery rates for performance.
   - Logging low-priority system events.
   - Cleaning up failed event triggers.
   - Polling distributed event buses for updates.
   - Handling delayed system notifications.
   - Processing low-priority system-wide broadcasts.
