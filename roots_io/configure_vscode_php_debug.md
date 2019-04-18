# Configure VS Code and the PHP Debug extension

https://roots.io/trellis/docs/debugging-php/

Trellis configures your Vagrant VM with PHP XDebug installed and listening on port `9000`. Simply configure your editor of choice to connect with the client. Even though XDebug is configured and ready to accept remote host debugging sessions, it is not automatically started. If you want the session to automatically start every time you `vagrant up`, include the following configuration option in `group_vars/development/php.yml`. Doing so will require you to re-provision your virtual machine: `vagrant reload --provision`.

```yaml
xdebug.remote_autostart: 1
```

If you just want to debug a script started through a web browser, simply add `?XDEBUG_SESSION_START=session_name` as parameter to the URL instead. For more information, read the [XDebug documentation](https://xdebug.org/docs/remote) on remote debugging.

## Visual Studio Code

In order to use XDebug under VS Code install the [PHP Debug extension](https://marketplace.visualstudio.com/items?itemName=felixfbecker.php-debug) by Felix Becker from the extension marketplace. Be sure to check out the documentation for configuration settings and the section on [Remote Host Debugging](https://marketplace.visualstudio.com/items?itemName=felixfbecker.php-debug#remote-host-debugging).

Now, To make VS Code map the files on the server to the right files on your local machine, you have to set the `pathMappings` settings in your `launch.json`:

```json
{
  "version": "0.2.0",
  "configurations": [
    {
      "name": "Listen for XDebug",
      "type": "php",
      "request": "launch",
      "port": 9000,
      "pathMappings": {
        "/srv/www/example.com/current": "${workspaceFolder}/site"
      }
    },
    {
      "name": "Launch currently open script",
      "type": "php",
      "request": "launch",
      "program": "${file}",
      "cwd": "${fileDirname}",
      "port": 9000
    }
  ]
}
```
