publiching docker images githubaction
https://docs.github.com/en/actions/publishing-packages/publishing-docker-images


ทำให้สามารถ run docker ได้โดยไม่ต้อง sudo 
1. sudo usermod -aG docker ${USER}
2. su - ${USER}
3. sudo service docker restart


ssh to linux server 
ลอง run : docker run -t -d -p 8080:8080 --name learn_autodeploy_gitactiondocker poowadon/learn_autodeploy_gitactiondocker:main

auto deploy ให้เขียน scripts
    nano update_docker.sh
    #! /bin/bash
    docker stop learn_autodeploy_gitactiondocker
    docker rm learn_autodeploy_gitactiondocker
    docker rmi poowadon/learn_autodeploy_gitactiondocker:main
    docker pull poowadon/learn_autodeploy_gitactiondocker:main

    docker run -t -d -p 8080:8080 --name learn_autodeploy_gitactiondocker poowadon/learn_autodeploy_gitactiondocker:main

add permission to update_docker.sh
    run `chmod +x update_docker.sh`