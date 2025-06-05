# Docker_Compose_Quickstart

1. From your project directory, start up your application by running docker compose up.

2. Enter http://localhost:8000/ in a browser to see the application running.

If this doesn't resolve, you can also try http://127.0.0.1:8000.

You should see a message in your browser saying:

        Hello World! I have been seen 1 times.

3. Refresh the page.

The number should increment.

        Hello World! I have been seen 2 times.

You can see it in the third commit.

4. Edit the compose.yaml file in your project directory to use watch so you can preview your running Compose services which are automatically updated as you edit and save your code.
Whenever a file is changed, Compose syncs the file to the corresponding location under /code inside the container. Once copied, the bundler updates the running application without a restart.

5. From your project directory, type docker compose watch or docker compose up --watch to build and launch the app and start the file watch mode.

 docker compose watch
[+] Running 2/2
 ✔ Container docs-redis-1 Created                                                                                                                                                                                                        0.0s
 ✔ Container docs-web-1    Recreated                                                                                                                                                                                                      0.1s
Attaching to redis-1, web-1
         ⦿ watch enabled
...

Check the Hello World message in a web browser again, and refresh to see the count increment.

6. To see Compose Watch in action:

    |.  Change the greeting in app.py and save it. For example, change the Hello World! message to Hello from Docker!:

            return f'Hello from Docker! I have been seen {count} times.\n'

    ||. Refresh the app in your browser. The greeting should be updated, and the counter should still be incrementing.


