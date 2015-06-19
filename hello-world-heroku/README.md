# Finatra Hello World Heroku Example Application

An example finatra application that highlights features of the [finatra-http](https://github.com/twitter/finatra/tree/master/http) framework that is deployable to [Heroku](https://heroku.com).

Run the example server on Heroku:
-----------------------------------------------------------

Copy the finatra/examples/finatra-hello-world directory contents (minus the .git directory) to another location locally.

```
$ cp -R finatra/examples/finatra-hello-world/ ~/finatra-hello-world
```

Intialize a git repository in the new directory location:

```
$ cd ~/finatra-hello-world
$ git init
Initialized empty Git repository in ~/finatra-hello-world/.git/
```

Create a `.gitignore` file (notice the newlines):

```
$ echo ".DS_Store
classes/
target/
sbt-launch.jar" > .gitignore
```

Commit all the files to master:

```
$ git add .
$ git commit -m "Initial commit."
```

Compile and stage the application:

```
$ ./sbt compile stage
```

Make sure you have the [Heroku Toolbelt](https://toolbelt.heroku.com/) [installed](https://devcenter.heroku.com/articles/getting-started-with-scala#set-up).

Create a new app in Heroku:

```
$ heroku create
Creating nameless-lake-8055 in organization heroku... done, stack is cedar-14
http://nameless-lake-8055.herokuapp.com/ | https://git.heroku.com/nameless-lake-8055.git
Git remote heroku added
```

Then deploy the example application to Heroku:

```
$ git push heroku master
Counting objects: 480, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (376/376), done.
Writing objects: 100% (480/480), 27.68 MiB | 16.24 MiB/s, done.
Total 480 (delta 101), reused 0 (delta 0)
remote: Compressing source files... done.
remote: Building source:
	...
```

You can then open the application in a browser with `heroku open`, e.g.:

```
heroku open hi?name=foo
```


Run the example locally with Foreman:
-----------------------------------------------------------

See the [Heroku documentation](https://devcenter.heroku.com/articles/getting-started-with-scala#run-the-app-locally) on running an app locally with Foreman.


```
$ PORT=8000 foreman start web
19:47:56 web.1  | started with pid 77663
19:47:59 web.1  | I 0528 02:47:59.058 THREAD1: HttpMuxer[/admin/metrics.json] = com.twitter.finagle.stats.MetricsExporter(<function1>)
19:47:59 web.1  | I 0528 02:47:59.096 THREAD1: HttpMuxer[/admin/per_host_metrics.json] = com.twitter.finagle.stats.HostMetricsExporter(<function1>)
19:47:59 web.1  | I 0528 02:47:59.183 THREAD1: Serving admin http on 0.0.0.0/0.0.0.0:0
19:47:59 web.1  | I 0528 02:47:59.218 THREAD1: Finagle version 6.25.0 (rev=78909170b7cc97044481274e297805d770465110)
19:48:00 web.1  | 2015-05-27 19:48:00,550 INF            HttpRouter                Adding routes
19:48:00 web.1  | GET     /hi
```

The app will now be running at [http://localhost:8000/hi?name=foo](http://localhost:8000/hi?name=foo). `Ctrl-C` to exit.
