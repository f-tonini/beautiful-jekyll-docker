## beautiful-jekyll-docker

Jekyll in a Docker container built on top of the beautiful-jekyll theme by Dean Attali (Github: [daattali](https://github.com/daattali/beautiful-jekyll))

## Docker Image Pull

Assuming **Docker** is installed, download this image using the following command:

```
docker pull ftonini/beautiful-jekyll-docker
```    

# Getting Started:

Follow these instructions (assumes you have **Git** installed on your system):
1. In the command line (CLI) navigate to your local directory where you want to store and develop your beautiful-jekyll website
    
    ```
    cd root/dir/of/your/jekyll/site
    ```

2. Clone my github repository using the following command:

    ```
    git clone https://github.com/f-tonini/beautiful-jekyll-docker.git
    ```        

3.  Navigate one level down into the folder created with the command at *step 2.*

    ```
    cd beautiful-jekyll-docker
    ```    

4. Create and run a Docker container locally using the following command:

    ```
    docker container run -d -p 4000:4000 --name my-jekyll-site -v ${pwd}:/srv/jekyll ftonini/beautiful-jekyll-docker
    ```
If the above command does not work, try replacing `${pwd}` with `"$PWD"`, hence:

    ```
    docker container run -d -p 4000:4000 --name my-jekyll-site -v "$PWD":/srv/jekyll ftonini/beautiful-jekyll-docker
    ```

# Getting Started: using Docker Compose

To make things even easier, you could also use my ```docker-compose.yml``` file, instead of using the set of istructions. The following steps assume you have **Docker Compose** and **Git** installed.

1. In the command line (CLI) navigate to your local directory where you want to store and develop your beautiful-jekyll website
    
    ```
    cd root/dir/of/your/jekyll/site
    ```

2. Clone my github repository using the following command:

    ```
    git clone https://github.com/f-tonini/beautiful-jekyll-docker.git
    ```        

3.  Navigate one level down into the folder created with the command at *step 2.*

    ```
    cd beautiful-jekyll-docker
    ```    

4. Create and run a Docker container locally using the following command:
   
    ```
    docker-compose up -d 
    ```

## How to Use

You should now have a running container. You can check this by running:

```
docker container ls -a
```

You should see a running container called *my-jekyll-site* (you can customize the container name by changing the ```--name``` option above). If you used ```docker-compose up``` the container will be automatically named based on your folder name (*beautiful-jekyll-docker_1*).

Preview your beautifull-jekyll site for testing/dev on your browser at ```http://localhost:4000```. If you want to preview the site at ```http://localhost```, 
make sure to replace ```-p 4000:4000``` with ```-p 80:4000``` inside the ```docker container run``` command above. Both ports are exposed in the original jekyll 
Dockerfile. 

If you now start editing the files inside the ```/web``` folder and refresh your browser (while the container is still running), you will see LIVE updates because the site is synced with the jekyll container volume. 

## Important Note on Gemfile and Gemfile.lock files

If you have an existing beautiful-jekyll site in a local directory, make sure both the Gemfile and Gemfile.lock files exist at the root of the directory. If not, the container will not be properly configured for a Jekyll site.

## Important Note on Local Preview on Browser

Depending on the structure and number of files in your site, it might take a few seconds for it to appear in the browser. Give it a few seconds and refresh the browser window
until the preview comes up.