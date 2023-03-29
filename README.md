# Ind-Ass2
 
![Rep is Public and has Unity Gitignore](https://user-images.githubusercontent.com/72412425/228298465-f1440dee-8c0d-4024-9bbc-33e494c2d588.png)
The Repository has been published as public and it has a unity gitignore. 


![Empty ](https://user-images.githubusercontent.com/72412425/228298993-353dbb24-393d-4eb1-a782-61e01483ab64.png)
Created an empty 3D Unity Project 

![Build Release](https://user-images.githubusercontent.com/72412425/228300350-f2225b47-5c7f-40d6-bde9-ec849bfc669b.png)
The Build has been created and Released in GitHub

Forward Rendering is the usual type of rendering technique that most engines use. Forward rendering starts with supplying the graphics card to the geometry which then gets projected and broken down to vertices, then it gets transformed or split into fragments, which then gets rendered and then passed onto the screen.

Deffered Rendering is when the rendering is deffered a little bit until all of the geometries have been passed down the pipe. The final image is then made by applying the shading at the end. 


My student number ends with an odd number. 

![Toon Water](https://user-images.githubusercontent.com/72412425/228616157-6af8b96f-16c8-4580-aa3b-ee6853b55c1f.png)

Added the Toon shader to the Water shader to make a toon like water. Added a low poly boat mesh that i found on the asset store to act like that boat that is shown in the pdf. The water shader I used was from the lecture as well as the Toon shader. I combined both shaders to have a Toon like Water shader which i then added to a plane object. I modified the shader so that it can have a sqaure wave to it. 

I combined the two shaders by copying the LightingToonRamp function from the ToonRamp shader we made in class and pasted it into the water shader that was also made in class. I then added a custom made toon texture and applied it to the disignated texture spot in the material.

![Screenshot 2023-03-29 103650](https://user-images.githubusercontent.com/72412425/228573793-555e9d95-e3fc-430e-aaa1-d611abcbeb9c.png)

The code takes an input image (RenderTexture Source) and generates a series of lower resolution versions of it. The variable "integerRange" specifies the amount by whihc the resolution is reduced at each step, and specifies how many steps are needed. It then applies a "Blit" operation, which is a type of image processing operation, to copy the input image to the currentDestination. The resulting tecture is then used as the input to the next iteration of the downsampling process. The code uses an array of RenderTextures "Textures" to store the results and then a new RenderTexture "currentDestination" is created to store the downscaled image. If the height scales beloew 2 pixels the downsampling process is stopped. After the downsampling is complete, the code generates a series of higher-resolution vaersions of the image. It does this by applying a "Blit" operation to each texture in the "textures" array, copying the results to the hnext higher resolution texture in the array. The highest resolution texture is copied to the ouput imageimage, the RenderTexture destination using another Blit operation. 


 ![Bloom On](https://user-images.githubusercontent.com/72412425/228581503-08ebf2d2-2c55-4512-a3ee-5c0837259973.png)
Added Bloom to the scene and in the image above, the bloom effect is in play. 

![Bloom Off](https://user-images.githubusercontent.com/72412425/228581654-542f670f-c719-420b-a2a6-60de313a628b.png)
This is how the boat looks when the bloom is not in play. 

![Shadow](https://user-images.githubusercontent.com/72412425/228581996-3d9a1dac-dc4b-434b-9219-d19c46c3bf36.png)
Added Shadows to the boat for task 4. I did this by using the previously created shadow shader from the lab. 


![Task 5 ](https://user-images.githubusercontent.com/72412425/228586196-31c10a31-8780-433f-825e-005085ed8081.png)

The following shader can be broken down into three parts.

PROPERTIES:

![Task 5 #1](https://user-images.githubusercontent.com/72412425/228586270-52880ebf-7e76-4a81-80d8-18aac97a4181.png)

This section defines all the necessary custom properties that can be set for the shader. In this case the properties used are 
"__Color_":  The main colour of the object which is defaulted to white. 
"__MainTex": A 2D Texture for the object's base colour. 
"__ShadowColor": the color of the object's shadow which again is defaulted to white. 

SUBSHADER:

![Task 5 #2](https://user-images.githubusercontent.com/72412425/228587424-30dde282-d450-4ed5-8240-1f1314c51ac0.png)

This section describes the behaviour of the shader during rendering. It includes tags to identify the object as opaque, a level of detail setting, and the CPGPROGRAM block which contains the actual code for the shader. 

CPGPROGRAM:

![Task 5 #3](https://user-images.githubusercontent.com/72412425/228587858-880be16e-fdb4-47fd-ae43-e5e5aa4fa179.png)

This section is where all the main shader code is defined. It stats with a prgma statement that defines the surface shader model being used, in this case it's CSLamber. It then declares three variable: MainTex, Color, and ShadowColor, which are used to access the values of the corresponding properties defined in the properties section. The struct input defines the inpt data that the shader will recieve for each pixel, in this case the shader receives the UV coordinates for the texture. The LightingCSLambert function calculates the lighting for the object, taking into accoung the surface output, including the albedo colour, and the light direction and attenuation. Lastly the surf function sets the output surface values, including the object's colour based on the texture and the "__Color" property. The code then ands with an ENDCG to indicate the end of the CPGPROGRAM block. Fallback Diffuse indicates the shader to fall back to the built in diffuse shader in case this custom shader is not supported. 


For the last task, the shader i chose is the Depth of Field shader and it looks like this

![ss](https://user-images.githubusercontent.com/72412425/228618357-7c8734e2-521c-4883-a0c0-dd56ba9d8684.png)

The shader has three passes that are used in order to get the depth of field effect. The Circle of Confusion Pass, Pre Filter Pass, and finally the Bokeh Pass.

![Screenshot 2023-03-29 141104](https://user-images.githubusercontent.com/72412425/228630084-3f722c30-e87c-4969-b769-5ce0f272b028.png)

The Circle of Confusion Pass calculates the circle of confusion of each pixel in the image, which is the blur radius that will be applied to it. the CoC is calculated based on the distance between the focus plane and each pixel's depth of value.

The Pre Filter Pass applies the pre filter to the image to rteduce any aliasing effects that can occur when the CoC is applied. it uses a 2D texture that contains the CoC values calculated in the previous pass.\

The Bokeh Pass applies the CoC to the image and simulates the lens blur effect. It uses a disk shaped kernel with a configurable number of samples to create the blur effect. The kernel samples are based on the distance from the center of the disk, with closer samples having a greater impact on the final colour value. 
 
