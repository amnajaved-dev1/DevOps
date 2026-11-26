# Lab 8: Docker Images, Container Networking, and Amazon ECR

**Execution environment:** Ubuntu Server (`amnajaved-dev1@ubuntu`)  
**Submission repository:** `DevOps`  
**Submission directory:** `Labs/Lab08`  
**Screenshot directory:** `Labs/Lab08/screenshots`

## Overview
This lab covers writing custom `Dockerfile` configurations using Ubuntu, building and running container images, serving a web page on port `3000`, comparing how `CMD` and `ENTRYPOINT` handle runtime arguments, and connecting containers by name on a custom Docker bridge network (`app-net`).

## Directory Structure
```text
DevOps/
└── Labs/
    └── Lab08/
        ├── README.md
        ├── task1/
        │   ├── Dockerfile
        │   └── myfile
        ├── task2/
        │   └── Dockerfile
        ├── task3/
        │   ├── cmd/
        │   │   └── Dockerfile
        │   └── entrypoint/
        │       └── Dockerfile
        └── screenshots/
            ├── task1_dockerfile.png
            ├── task1_image_build.png
            ├── task1_image_run.png
            ├── task1_container_logs.png
            ├── task2_web_files.png
            ├── task2_image_build.png
            ├── task2_container_running.png
            ├── task2_webpage.png
            ├── task3_cmd_dockerfile.png
            ├── task3_cmd_build.png
            ├── task3_cmd_run.png
            ├── task3_entrypoint_dockerfile.png
            ├── task3_entrypoint_build.png
            ├── task3_entrypoint_run.png
            ├── task4_network_setup.png
            ├── task4_alpine_ping.png
            ├── task4_alpine_http.png
            ├── task4_ubuntu_packages.png
            ├── task4_ubuntu_http.png
            ├── task4_ubuntu_ping.png
            ├── task4_network_inspect.png
            └── task4_network_cleanup.png

```

## Lab Objectives

* Use `FROM`, `LABEL`, `COPY`, `RUN`, `ADD`, `WORKDIR`, and `CMD` in a `Dockerfile`.
* Build and run a custom Docker image, then inspect container logs.
* Configure `ENV` and `EXPOSE` and publish a container port with `-p`.
* Keep a container running by starting a Python HTTP server as its main process.
* Compare `CMD` and `ENTRYPOINT` behavior when running images with and without extra arguments.
* Create a custom Docker bridge network, verify container-to-container communication by name, inspect network details, reconnect a container, and clean up all resources.

## Completed Tasks

### Task 1: Build an Ubuntu Image that Prints a File (`my-ubuntu:1.0`)

* Created `task1/myfile` and `task1/Dockerfile` using `FROM ubuntu`, `COPY`, `RUN`, `ADD`, `WORKDIR /app`, and `CMD ["cat", "myfile"]`.
* Built `my-ubuntu:1.0`, ran `my-ubuntu-demo`, and verified output via `docker logs my-ubuntu-demo`.

### Task 2: Serve an HTML Page on Port 3000 (`my-ubuntu:1.1`)

* Created `task2/Dockerfile` installing `python3`, setting `ENV PAGE_TITLE="DevOps"`, generating `index.html`, exposing port `3000`, and running `python3 -m http.server 3000 --bind 0.0.0.0`.
* Built `my-ubuntu:1.1`, started `my-ubuntu-web` with `-p 3000:3000`, and verified the rendered webpage in the browser.

### Task 3: Compare `CMD` and `ENTRYPOINT`

* **CMD (`my-image:cmd`):** Confirmed default execution prints `Hello from CMD`, while passing `ls -l` overrides the `CMD` instruction.
* **ENTRYPOINT (`my-image:entrypoint`):** Confirmed default execution prints `Hello from ENTRYPOINT`, while passing `goodbye` appends the argument (`Hello from ENTRYPOINT goodbye`).

### Task 4: Connect Containers with a Docker Network (`app-net`)

* Created custom bridge network `app-net` and started `nginx` (`nginx:alpine`) on `app-net`.
* Verified DNS name resolution and HTTP connectivity to `http://nginx` from both a temporary `alpine` container and an interactive `ubuntu-app-net` container (`ping` and `curl`).
* Inspected `app-net` configuration, disconnected and reconnected `nginx`, and cleaned up both containers and the custom network.

## Final Submission Checklist

* [x] Task 1 contains `Dockerfile` and `myfile`.
* [x] Task 2 contains `Dockerfile` with `ENV PAGE_TITLE` and `RUN echo` to generate `index.html` inside the image.
* [x] Task 3 contains separate `cmd/Dockerfile` and `entrypoint/Dockerfile` files.
* [x] All four Docker images built successfully with the required tags.
* [x] The first container printed both lines and its logs show the same output.
* [x] `my-ubuntu-web` ran and the webpage was verified on port `3000`.
* [x] Task 3 shows the default `CMD`, its replacement by `ls -l`, and both `ENTRYPOINT` runs.
* [x] Task 4 shows successful `ping` and HTTP requests to `nginx` from Alpine and Ubuntu, plus network inspection and cleanup.
* [x] All 22 guided-task screenshots use the exact filenames in `Labs/Lab08/screenshots/`.
* [x] Complete `DevOps/Labs/Lab08` directory pushed to GitHub.

```

<ElicitationsGroup message="Once you paste and save README.md, finish pushing your lab:">
  <Elicitation label="Give me the final git push commands" query="I pasted README.md and moved all 22 screenshots into Labs/Lab08/screenshots. Give me the git add, commit, and push commands."/>
  <Elicitation label="Help me transfer screenshots via scp" query="Give me the exact scp command from Windows Command Prompt to copy my 22 screenshots into ~/DevOps/Labs/Lab08/screenshots on Ubuntu."/>
</ElicitationsGroup>

```
