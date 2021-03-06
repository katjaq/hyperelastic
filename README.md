# hyperelastic
Javascript simulations of hyperelastic materials submitted to growth.

The interface presents various presets illustrating different geometries and growth functions. After selecting a preset, its parametres can be changed to test their different effects. The mechanical parametres are shared by all models. They include the bulk modulus (K) and the shear modulus (mu). Addditionally, there's the material's density (rho) and the viscosity of the simulation (gamma).

<img src="https://user-images.githubusercontent.com/6297454/37560725-fc0d6aee-2a3d-11e8-9231-dfa0578b4583.gif" width="420"> <img src="https://user-images.githubusercontent.com/6297454/37560727-02d72ca2-2a3e-11e8-8099-6a17f62b447b.gif" width="420">

For the ring, the geometry parametres are:

* Ri: Inner radius in mm
* Ro: Outer radius in mm
* th: ring thickness
* d: size of a typical tetrahedron. Ri, Ro and th have to be multiples of this value.

For the block, the geometry parametres are:

* Width: block width in mm
* Height: block height in mm
* Depth: block depth in mm
* d: length of a typical tetrahedron. Width, Height and Depth have to be multiples of d.

The example of an ellipsoid:

<img src="https://user-images.githubusercontent.com/6297454/37560922-aadad69e-2a41-11e8-871b-c7a106517bbc.gif" width="420"> <img src="https://user-images.githubusercontent.com/6297454/37560923-aaee4cd8-2a41-11e8-8915-2ce1b18583b1.gif" width="420">

Render options:
* Wireframe: whether to display the objects in wireframe or not
* Perspective: whether to use perspective rendering or orthographic
* colormap: two colormaps are currently available. The 'normal' colormap colours each face according to its normal vector. The 'deformation' colormap colours each face according the the material deformation of each the object relative to the rest reference volume. The colour map goes from black for the most contracted elements to white for the most dilated elements.

After each change in parametres click 'Restart' to launch a new simulation.

## How to add a new geometry to the code (for developers)

These are the steps that were required to add the block geometry and the Block Border preset (and may be required to add another geometry)

to geometry.js
* add makeBlock()
* add blockTetra()
* add blockVind()

to growth.js
* add growBlockBorderInstantaneous()

to presets.js
* add a preset demonstrating the use of the geometry (optional)

to index.html
* add preset to the list of presets (if a preset had been added)
* add to the switch of handled url arguments  (if a preset had been added)
* add to the getPresetParams function (required, even if no new preset has been added)

to simulation.js
* add geometry to switch in initSimulation()
* add growth function to switch in initSimulation()

to display.js
* add block_deformationColor()

nothing to add to mechanics.js or to algebra.js
