1. Start the vertual machine.
    ```
    $ vagrant up
    ```
1. Check vertual machine OS.
    ```
    $ vagrant ssh
    $ cat /etc/redhat-release 
    ```
1. Install podman.
    ```
    $ cd ansible/
    $ ansible-playbook -i hosts site.yml
    ```
1. Build docker image.
    ```
    $ cd java/demo/
    $ docker build -t podman_demo:latest .
    ```
1. Create a tag.
    ```
    $ docker tag podman_demo:latest ${your docker id}/podman_demo:latest
    ```
1. Push docker image.
    ```
    $ docker push ${your docker id}/podman_demo:latest
    ```
1. Pull docker image.
    ```
    # podman pull ${your docker id}/podman_demo:latest
    ```
1. Launch container.
    ```
    podman run --name podman_demo -p 8080:8080 -itd docker.io/${your docker id}/podman_demo:latest
    ```