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




Split up your services

1. In your project folder, create a new Compose file called infra.yaml.

2. Cut the Redis service from your compose.yaml file and paste it into your new infra.yaml file. Make sure you add the services top-level attribute at the top of your file. Your infra.yaml file should now look like this:

    services:
      redis:
        image: "redis:alpine"

3. In your compose.yaml file, add the include top-level attribute along with the path to the infra.yaml file.

    include:
    - infra.yaml
    services:
    web:
        build: .
        ports:
        - "8000:5000"
        develop:
        watch:
            - action: sync
            path: .
            target: /code

4. Run docker compose up to build the app with the updated Compose files, and run it. You should see the Hello world message in your browser.



This is a simplified example, but it demonstrates the basic principle of include and how it can make it easier to modularize complex applications into sub-Compose files. 