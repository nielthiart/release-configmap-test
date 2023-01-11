## Steps to reproduce

1.  Clone/fork https://github.com/nielthiart/release-configmap-test repo.
2.  Create new Release app using `./.relesae/application_template.yaml`.
3.  Build and deploy the app.
4.  Edit the *Environment Configuration*, add this to the `configmap` array:
    ```yaml
    - mount_path: "/etc/configmaptest/file3.txt"
      repo_path: "./file3.txt"
      name: file-three
    ```
5.  Save and apply new configuration.
6.  Wait for deloyment to finish.
7.  Open `busyexample` service terminal.
8.  Run:
    ```sh
    ls -F /etc/configmaptest/
    ```

## Input

```sh
ls -F /etc/configmaptest/
```

## Expected output

```
file1.txt* file2.txt* file3.txt*
```

## Actual output

```
file1.txt* file2.txt* file3.txt/
```