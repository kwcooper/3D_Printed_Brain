# 3D PRINT YOUR BRAIN 
By Keiland Cooper (November 2016 version)

Some Information on how I 3D printed my brain from structural MRI images 
(Not actual size)

![Picture of me holding my 3D printed brain](my3d.jpg?raw=true "My 3D Printed Brain")


## Programs needed:

* [Freesurfer](http://freesurfer.net/) -open source mri software
* [MRIcron](http://people.cas.sc.edu/rorden/mricron/index.html) (needs NIFTI format) or matlabs version -easily convert images
* [meshlab](http://meshlab.sourceforge.net/) or [autodesk](http://www.autodesk.com/) -open source stl viewer and manipulator


## My Notes

1. Convert the MRI images, freesurfer was weird with dicoms for some-reason
    1. test out different micron settings, this will depend on the type of scanner used
    2. I think i ended up going with SFL/SPM8, I need to read up more on this though
    3. (Something funny happened to me with dti vs normal imaging around this or the next step)
2. Process the images in freesurfer
    1. `recon-all -s {your name here} -all -i {path to your newly converted file}`
    2. this will process for awhile (no really, took like 16+ hours on my MBP)
    3. to convert pial to stl etc. `mris_convert {path to freesurfer}/subjects/mybrain/surf/ rh.pial rh.stl`
    4. use the same code with the lh.pial to lh.stl
3. Import the stl’s into meshlab or whatever software you choose
    1. Run a smoothing algorithm on it and maybe reconstruct if the file is unseemly large
5. Print the STL
    1. It’s easiest to print hemisphere by hemisphere, then glue


## Helpful links 

* [MRI Imaging Info](https://en.wikipedia.org/wiki/Magnetic_resonance_imaging)
* [freesurfer](http://freesurfer.net/) (and [this](http://freesurfer.net/fswiki) was the most helpful page)
* Some [forums](https://surfer.nmr.mgh.harvard.edu/fswiki/recon-all) on freesurfer from harvard detailing the steps freesurfer is doing
* some file converter info from [mathworks](https://www.mathworks.com/matlabcentral/fileexchange/42997-dicom-to-nifti-converter--nifti-tool-and-viewer)


## Debugging

* I had to move the free surfer install to the documents folder due to permissions errors, sudo wouldn’t fix it...
* use the [mail archives](https://mail.nmr.mgh.harvard.edu/pipermail//freesurfer/2012-July/024750.html) to fix errors 
* make sure the tutorials work on your machine first, this could save a lot of time (trust me)
* `recon-all` is amazing and will automate pretty much everything, especially the scull stripping stage, and was fun to read about


## TODO for the next time
* figure out how to print the [cerebellum](https://mail.nmr.mgh.harvard.edu/pipermail//freesurfer/2016-May/045371.html) with free surfer (I don’t want the 3D me to be shaky)
* use [mri_tessellate](https://surfer.nmr.mgh.harvard.edu/fswiki/tessellate)?
* figure out the problems with the DTI anatomy [images](https://mail.nmr.mgh.harvard.edu/pipermail//freesurfer/2012-July/024750.html)
* print my DTI connectome
* Print specific brain regions
* Automate with python code
