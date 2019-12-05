# Shape from shading
This work was part of a C++ school project. You can find the original handout (in french) in __doc__ folder.

## Introduction

The __shape from shading__ (sfs) is a computer vision problem that involves rebuilding the
relief of a scene from a single picture of it. The sfs was initiated in the 60s by the astronomer Rindfleish, with the publication of an article on the tomography of the moon. However,it was only in the 1970s with Horn and Brooks that sfs became a field of study in its own right. The authors focused on both the physical modeling of the problem, the uniqueness of the solution and the numerical methods of resolution. Their book still serves as a reference. 

### Modelization 
In this project, we consider that the gray level of the image depends only on the direction of the incident light and the normal on the surface (Lambertian shading model):

![equation](http://www.sciweavers.org/tex2img.php?eq=%24%24I%28x%2C%20y%29%3D%5Cboldsymbol%7BL%7D%20%5Ccdot%20%5Cboldsymbol%7Bn%7D%28x%2C%20y%29%24%24%0A&bc=White&fc=Black&im=jpg&fs=12&ff=arev&edit=0)

with __I__ the intensity of the shading (usually __I__ ∈ [0; 255]), __L__ the direction of incident light and n the outgoing unit normal. The main problem for the resolution is its nonlinearity which comes simply from the normalization of __n__. Assuming that the source is in (0,0,1) ("frontal" lighting) and the intensity being maximal when __n__ and __L are parallel, one can rewrite the equation, after normalization, as the eikonal equation (3).
### Resolution 
The (deterministic) optimization methods for sfs consist in minimizing functionalities representing the likelihood between the directional derivatives of a surface for the luminance equation. Two penalty terms are usually added. The first ensures the integrability of
the solution, basic hypothesis of our modeling (Schwartz's condition on derivatives), the second penalizes non-smooth solutions. We discretise the previous functionalities by finite differences off-center on the righ.
The challenge of this project was to implement in C++ the resolution of optimization problems (5) and (6) related to sfs using the L-BFGS algorithm. We also wrote an ImageFactory class to create images tests from analytical or discrete 3D surfaces.

## Generate the binary using the makefile
```
make
```

## Cleaning objects and binary
```
make clean
``` 
## Run the program 
``` 
./bin/app
```

## Visualization of meshes
Using the Vizir software (made by [Adrien Loseille](http://pages.saclay.inria.fr/adrien.loseille/)) present in mesh folder