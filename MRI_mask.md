Magnetic resonance imaging (MRI) is a medical imaging technique used in radiology to form pictures of the anatomy and the physiological processes of the body, in this case, the brain. An MRI scan uses voxels (3D pixels) with varying intensities. It can be difficult to separate these voxels for data analysis, so we use a technique called **masking**. Masking allows us to isolate the voxels that we are interested in from those that we are not by applying a *threshold* value. 

First, we must import the library imageio. Imageio is a Python library that provides an easy interface to read and write a wide range of image data, including animated images and volumetric data. Additionally, we need to import numpy and matplotlib.pyplot. 


```python
import imageio
import numpy as np
import matplotlib.pyplot as plt
```

Next we will read in the image using the function imageio.imread():


```python
brain_img = imageio.imread('Anat001.20040930.142737.2.MPRAGE_T1_SAGITTAL.0080.dcm')
```

Now lets look at the image prior to the mask using the function plt.imshow(), in grey coloring: 


```python
plt.imshow(brain_img, cmap = 'gray')
plt.axis('off')
plt.show()
```




    
![png](MRI_mask_files/MRI_mask_6_0.png)
    



We can see that there is not a strong distinction between the grey coloring of the brain scan and the black background. Lets change that. We will apply a mask onto the image using the np.where() function, where any voxels in the brain_img that are *GREATER* than 125 will equal to 1, and all other voxels will equal to 0. 


```python
brain_mask = np.where(brain_img > 125, 1, 0)
plt.imshow(brain_mask, cmap = 'gray')
plt.axis('off')
plt.show()
```




    
![png](MRI_mask_files/MRI_mask_8_0.png)
    



Again, we used the function plt.imshow() to view the image in grey coloring, however, this time, there is a LARGE distinction between the black background and the brain scan. This mask allows us to see the structure of the brain more clearly, and will make it easier to perform an analysis on this scan. 
