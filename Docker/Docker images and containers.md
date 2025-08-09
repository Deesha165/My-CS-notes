- image is the sharable package that contains setups and code instructions
- container is the running unit of software and multiple containers can be made based on one image.
![[Screenshot 2025-07-14 215536.png]]

- image is read only meaning is that it is once built any change of code doesn't reflect and you must build it again to reflect the code changes
- order of layers is important becuese it affects execution time as layers with no changes are cached and if change detected at one layer all subsequent ones would be executed 
- In Docker, **attaching** refers to **connecting your terminal** to a **running container's standard input/output (stdin/stdout/stderr)** so you can:

- **See logs/output live**
    
- **Interact with the container (if it's interactive)**