# Lab 7: Docker Containers and Images

*Execution environment:* Your assigned Ubuntu server  
*Submission repository:* DevOps  
*Submission directory:* Labs/Lab07  
*Screenshot directory:* Labs/Lab07/screenshots  

Install Docker and Docker Compose on your Ubuntu server if they are missing. If both tools are already installed, go directly to the version checks in Task 1. Then run PostgreSQL and NGINX in Docker, manage containers and images, and save changes from an NGINX container to a new image.

DevOps/  
└── Labs/  
    └── Lab07/  
        ├── README.md  
        └── screenshots/  
            ├── docker_installation.png  
            ├── postgres_missing_password.png  
            ├── postgres_96_running.png  
            ├── postgres_both_versions.png  
            ├── docker_info.png  
            ├── docker_search_ubuntu.png  
            ├── ubuntu_container_status.png  
            ├── postgres_96_cleanup.png  
            ├── nginx_containers_started.png  
            ├── nginx_latest_page.png  
            ├── nginx_older_page.png  
            ├── nginx_latest_logs.png  
            ├── nginx_attach_detach.png  
            ├── nginx_exec_shell.png  
            ├── nginx_diff.png  
            ├── nginx_inspect.png  
            └── nginx_commit.png  

## Lab Objective

By the end of the published tasks, you will be able to:
- Install Docker Engine and the Docker Compose plug-in on Ubuntu if needed.
- Check the installed Docker and Docker Compose versions.
- Pull a PostgreSQL image by its tag and identify a missing initialization password.
- Start two PostgreSQL containers in the background and identify their image tags with `docker ps`.
- Inspect the Docker installation, list local images, and search Docker Hub.
- Compare running and stopped containers, then restart, stop, and remove a lab container and remove its image tag.
- Run two NGINX containers on different host ports, open both welcome pages, and view the container logs.
- Attach to the main process, open a separate shell, inspect filesystem changes, and save a new image.

## Task List

- Task 1: Install Docker and Docker Compose
- Task 2: Run Two PostgreSQL Versions in Docker
- Task 3: Inspect Docker and Manage Containers and Images
- Task 4: Run Two NGINX Containers on Different Ports
- Task 5: Work Inside a Container and Save a New Image
