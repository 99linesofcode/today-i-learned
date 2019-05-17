# Manually triggering wp-cron

Trellis and Bedrock are configured to `DISABLE_WP_CRON` by default. Instead of depending on wp-cron, a system cronjob is setup to run ever 15 minutes, executing the [WP CLI](https://developer.wordpress.org/cli/commands/cron/event/run/) command `wp cron event run --due-now`.

When attempting to debug this scenario, I found that breakpoints in my application were not triggered. It was said in this [this stackoverflow question](https://stackoverflow.com/questions/41047039/wp-cron-event-firing-but-doesnt-hit-breakpoint-in-debug/42146616#42146616) that is because the `DEBUG_SESSION_START` parameter is not present in the request's header. Sadly, I was not able to get the example code that this `$_GET` parameter through a filter on `wp_cron_request`.

Later, I learned that WordPress has a script that gets called to execute events that are due and can be found at the following URL:

`http://example.com/wp/wp-cron.php?doing-cron`

Simply set your breakpoints and make a GET request to the URL above and the XDebug remote server will be triggered as it normally would.
