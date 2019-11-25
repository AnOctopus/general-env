# Why Docker?
For solving our dev env problem, I knew we needed to run software in very standardized, consistent environments. Docker is easy to set up and use, and lower overhead than VMs. Docker also has a fairly limited, easy to learn set of quirks and failure modes, which helps a lot with getting things set up fast and reducing effort to debug issues.

Relatedly, having a small, standard set of tools and technologies we use across clients reduces the effort overhead of getting set up. It also makes it easier to shift to using docker in CI and staging/production.

# What is the goal?
Every client's project should be easy, fast, and reliable to set up. Ideally we could clone a repo, open the README, and run the one line in the instructions and have the project running in a matter of minutes (or tens of minutes for those of us with very slow computers). If we can't do this, then I'm not giving us the development experience we should have.

# What do we do?
Every application gets a Dockerfile. Projects with multiple appications (such as a frontend and backend) get one for each. 

For most projects, we'll use docker-compose to run the applications locally, including the database. Where possible, the source code will be mounted in the container to take advantage of server hotloading. Applications that are deployed to kubernetes will instead be engineered to run locally in minikube, with helm configurations to make that easy.

