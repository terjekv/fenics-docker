# dolfin-adjoint stable version image

This image provides the most recent stable release of dolfin-adjoint
(<http://dolfin-adjoint.org>). The FEniCS installation is built
against the stable image
(<https://hub.docker.com/r/fenicsproject/stable/>) which contains
up-to-date stable build of FEniCS, PETSc and SLEPc.

To launch the container:

    docker run -t -i fenicsproject/dolfin-adjoint:latest

To share a specified directory from the host with the container:

    docker run -v /absolute/path/to/shared/directory:/home/fenics/shared -t -i fenicsproject/dolfin-adjoint:latest