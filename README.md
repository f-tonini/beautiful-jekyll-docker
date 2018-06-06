# beautiful-jekyll-docker

Jekyll in a Docker container built on top of the beautiful-jekyll theme by Dean Attali (Github: [daattali](https://github.com/daattali/beautiful-jekyll))

## Getting Started

Download this image using the following command:

```
docker pull ftonini/beautiful-jekyll-docker
```    

Assuming Docker and Docker Compose are installed, make sure you navigate to your local dir where the jekyll site will be sitting:

```
cd dir/of/your/jekyll/site
```

Then, on Linux/Mac use the following command to run the downloaded image:

```
docker container run -d -p 4000:4000 --name beautiful-jekyll -v $(pwd):/srv/jekyll ftonini/beautiful-jekyll-docker
```

Or the following if using Windows PowerShell:

```
docker container run -d -p 4000:4000 --name beautiful-jekyll -v ${pwd}:/srv/jekyll ftonini/beautiful-jekyll-docker
```

## How to Use

By using ```$(pwd)``` it will mount your current path into the containers ```/srv/jekyll```. 
You should now have a running container called *beautiful-jekyll* (you can customize the container name by changing the ```--name``` option above). 
Preview your beautifull-jekyll site for testing/dev on your browser at ```http://localhost:4000```. If you want to preview the site at ```http://localhost```, 
make sure to replace ```-p 4000:4000``` with ```-p 80:4000``` inside the ```docker container run``` command above. Both ports are exposed in the original jekyll 
Dockerfile. 

## Important Note on Gemfile and Gemfile.lock files

If you have an existing beautiful-jekyll site in a local directory, make sure both the Gemfile and Gemfile.lock files exist at the root of the directory. If not, the container will not be properly 
configured for a Jekyll site.

## Important Note on Local Preview on Browser

Depending on the structure and number of files in your site, it might take a few seconds for it to appear in the browser. Give it a few seconds and refresh the browser window
until the preview comes up.

