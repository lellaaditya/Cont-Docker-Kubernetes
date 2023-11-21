Vitualization: `Virtual Machine which is works as a software based on Physical Server`
Hypervisor: 
Container:


3 ways to reduce the size of your Docker Images

If you’re reading this, chances are you’re running very large Docker containers in production.
A Container that’s several gigabytes in size slows deployments, increases bandwidth & storage costs and consumes valuable time of developers.


So here’s how you make Docker Images slimmer:

👉 Leverage Multi-stage builds
Multi-stage builds separate the build environment from the final runtime environment. They allow you to compile & package your application in one stage and then copy only the necessary artifacts to the final image, reducing its size significantly.
You'd typically combine these with a Light base Image as your final one (can you give me examples of such images?)
I made a small video on how to do this 🔗 youtu.be/hyLCBj1ko98


👉 Build Images from Scratch
If you only need to run a statically-compiled, standalone executable (like a C++ or Go application), pack it inside an empty Image by using “scratch” as the base image.
🔗 doc - https://lnkd.in/gxT2GTCX


👉 Use fewer Layers
Each instruction like RUN or COPY adds another layer to your image, thus increasing its size. Each layer comes with its own metadata & file system structures. The fewer layers you use, the lesser data overhead your image has.
🔗 doc https://lnkd.in/eNkvGHAa


Have you found any other size reduction strategies that work for you?


ps- If you want to learn how to use Docker effectively, I teach it in my video 🔗 youtu.be/UxJsBW7nYfo
