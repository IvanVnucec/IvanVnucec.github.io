---
title: "Catchcam: Enclosure Design and 3D Printing"
categories:
  - Blog
tags:
  - catchcam
header:
  image: /assets/images/enclosure_freecad_vs_print.png
cura_gallery:
  - url: /assets/images/enclosure_in_cura.png
    image_path: /assets/images/enclosure_in_cura.png
  - url: /assets/images/enclosure_in_cura_sliced.png
    image_path: /assets/images/enclosure_in_cura_sliced.png
freecad_gallery:
  - url: /assets/images/enclosure_freecad_all_top.png
    image_path: /assets/images/enclosure_freecad_all_top.png
  - url: /assets/images/enclosure_freecad_all_bottom.png
    image_path: /assets/images/enclosure_freecad_all_bottom.png
  - url: /assets/images/enclosure_freecad_bottom.png
    image_path: /assets/images/enclosure_freecad_bottom.png
  - url: /assets/images/enclosure_freecad_top.png
    image_path: /assets/images/enclosure_freecad_top.png
  - url: /assets/images/enclosure_freecad_split_surface.png
    image_path: /assets/images/enclosure_freecad_split_surface.png
enclosure_print_1_gallery:
  - url: /assets/images/enclosure_print_1_1.jpeg
    image_path: /assets/images/enclosure_print_1_1.jpeg
  - url: /assets/images/enclosure_print_1_2.jpeg
    image_path: /assets/images/enclosure_print_1_2.jpeg
  - url: /assets/images/enclosure_print_1_3.jpeg
    image_path: /assets/images/enclosure_print_1_3.jpeg
  - url: /assets/images/enclosure_print_1_4.jpeg
    image_path: /assets/images/enclosure_print_1_4.jpeg
  - url: /assets/images/enclosure_print_1_5.jpeg
    image_path: /assets/images/enclosure_print_1_5.jpeg
  - url: /assets/images/enclosure_print_1_6.jpeg
    image_path: /assets/images/enclosure_print_1_6.jpeg
  - url: /assets/images/enclosure_print_1_7.jpeg
    image_path: /assets/images/enclosure_print_1_7.jpeg
  - url: /assets/images/enclosure_print_1_8.jpeg
    image_path: /assets/images/enclosure_print_1_8.jpeg
  - url: /assets/images/enclosure_print_1_9.jpeg
    image_path: /assets/images/enclosure_print_1_9.jpeg
  - url: /assets/images/enclosure_print_1_10.jpeg
    image_path: /assets/images/enclosure_print_1_10.jpeg
  - url: /assets/images/enclosure_print_1_11.jpeg
    image_path: /assets/images/enclosure_print_1_11.jpeg
  - url: /assets/images/enclosure_print_1_12.jpeg
    image_path: /assets/images/enclosure_print_1_12.jpeg
  - url: /assets/images/enclosure_print_1_13.jpeg
    image_path: /assets/images/enclosure_print_1_13.jpeg
  - url: /assets/images/enclosure_print_1_14.jpeg
    image_path: /assets/images/enclosure_print_1_14.jpeg
  - url: /assets/images/enclosure_print_1_15.jpeg
    image_path: /assets/images/enclosure_print_1_15.jpeg
  - url: /assets/images/enclosure_print_1_16.jpeg
    image_path: /assets/images/enclosure_print_1_16.jpeg
  - url: /assets/images/enclosure_print_1_17.jpeg
    image_path: /assets/images/enclosure_print_1_17.jpeg
  - url: /assets/images/enclosure_print_1_18.jpeg
    image_path: /assets/images/enclosure_print_1_18.jpeg
  - url: /assets/images/enclosure_print_1_19.jpeg
    image_path: /assets/images/enclosure_print_1_19.jpeg
  - url: /assets/images/enclosure_print_1_20.jpeg
    image_path: /assets/images/enclosure_print_1_20.jpeg
  - url: /assets/images/enclosure_print_1_21.jpeg
    image_path: /assets/images/enclosure_print_1_21.jpeg
  - url: /assets/images/enclosure_print_1_22.jpeg
    image_path: /assets/images/enclosure_print_1_22.jpeg
  - url: /assets/images/enclosure_print_1_23.jpeg
    image_path: /assets/images/enclosure_print_1_23.jpeg
enclosure_print_2_gallery:
  - url: /assets/images/enclosure_print_2_1.jpeg
    image_path: /assets/images/enclosure_print_2_1.jpeg
  - url: /assets/images/enclosure_print_2_2.jpeg
    image_path: /assets/images/enclosure_print_2_2.jpeg
  - url: /assets/images/enclosure_print_2_3.jpeg
    image_path: /assets/images/enclosure_print_2_3.jpeg
  - url: /assets/images/enclosure_print_2_4.jpeg
    image_path: /assets/images/enclosure_print_2_4.jpeg
  - url: /assets/images/enclosure_print_2_5.jpeg
    image_path: /assets/images/enclosure_print_2_5.jpeg
diffuser_pipes_gallery:
  - url: /assets/images/enclosure_print_1_10.jpeg
    image_path: /assets/images/enclosure_print_1_10.jpeg
  - url: /assets/images/enclosure_print_1_11.jpeg
    image_path: /assets/images/enclosure_print_1_11.jpeg
  - url: /assets/images/enclosure_print_1_12.jpeg
    image_path: /assets/images/enclosure_print_1_12.jpeg
---

After an extensive search for a suitable off-the-shelf enclosure, I decided to design and 3D print a custom enclosure for my Catchcam project. My requirements were specific: a small and easy-to-assemble enclosure. I wanted to avoid the hassle of modifying a generic enclosure by drilling holes and cutting openings. By designing my own enclosure, I could ensure a perfect fit for my project's needs.

**Note:** If you're interested, you can pre-order a sample at [vnucec.ivan@gmail.com](mailto:vnucec.ivan@gmail.com).
{: .notice--warning}

## Design Inspiration

The main inspiration for the enclosure design came from the [Digilent Analog Discovery 3](https://digilent.com/reference/test-and-measurement/analog-discovery-3/start) device. I really liked the look and feel of that enclosure, especially the rounded edges and the overall simplicity of the design. I decided to adopt a similar design for my Catchcam project.

{% include figure popup=true image_path="/assets/images/digilent_analog_discovery_3.png" caption="Digilent Analog Discovery 3. Courtesy of digilent.com." %}

## Design Process

The enclosure is designed in [FreeCAD](https://www.freecad.org/) which is a free and open-source parametric 3D CAD software. It took me a while to get used to the software, but I'm quite happy with the results. Although I have some experience with [CATIA](https://www.3ds.com/products/catia), I've decided to go with FreeCAD because it's free and open-source. The journey was quite challenging because FreeCAD has a few quirks and you need to get used to the way it works. Also, FreeCAD was crashing quite often without any warning, so I had to save my work every time I've made some significant changes. Actually, the main frustration was that they had published a first major release v1.0 which implies that the software is stable, but it's far from it. I've also tried [OpenSCAD](https://openscad.org/) which is a script-based 3D CAD software because I love the idea that you can create 3D models using code, however, for complex shapes like the enclosure, the OpenSCAD code would be too complex to manage.

Catchcam enclosure dimensions are 65x65x18 mm. The enclosure is designed to be 3D printed in two parts: the top, and the bottom part. The top and bottom dividing plane cuts trough the middle of the USB-C, LEDs and the Volume rotary knob because those parts are sticking out of the PCB and I aimed to make assembly as easy as possible. The bottom part of the enclosure has a circular cutout for the speaker while the top part is solid. The two parts are held together with four ISO 7046 M3x14 screws located in the corners of the enclosure. The enclosure will be printed in PLA, but I might try printing it in ABS or PETG for better durability.

{% include gallery id="freecad_gallery" caption="Catchcam enclosure in FreeCAD." %}

### Design Iterations

The first prototype of the enclosure had screws located at the top of the enclosure, but I've decided to move them to the bottom because I wanted to make the top part as clean as possible. The screw holes are designed to be self-tapping so the screws can be screwed directly into the plastic without the need for a nut. I've also added a small chamfer to the screw holes so the screws can be easily screwed in. For the next iteration of the enclosure, I would like to avoid using screws for assembly and try to design a snap-fit mechanism.

{% include figure popup=true image_path="/assets/images/enclosure_freecad_exploded.png" caption="Catchcam enclosure exploded view." %}

### LED Diffuser Pipes

I've also added circular cutouts for the LEDs in order to include small plastic light diffuser pipes in order to make the LEDs more visible. The diffuser pipes are glued to the enclosure with a small amount of super glue.

{% include gallery id="diffuser_pipes_gallery" caption="Catchcam enclosure with the diffuser pipes." %}

As you saw in the image above, the diffuser pipes holes are splitted in half for easier assembly, however, I would like to experiment with a solid hole in the future so the diffuser pipes can be pressed in without the need for glue. Moreover, I have a problem with the diffuser pipes because they are not the right length and they are interfering with the LEDs so I need to grind them down a bit in order to make them fit nicely.

### Antenna Considerations

I've especially paid attention to the distance between the PCB and the top part of the enclosure because of findings in the [Molex GPS Ceramic Antenna](https://tools.molex.com/pdm_docs/as/2088900001-AS.pdf) application specification document where the GNSS antenna performance can be affected by the distance between the antenna and the ground plane. Currently, the distance is around 6.37 mm and that seems to be working fine.

{% include figure popup=true image_path="/assets/images/enclosure_freecad_antenna.png" caption="Catchcam enclosure with the GNSS antenna." %}

## 3D Print and Assembly

The top and bottom parts of the enclosure are meant to be printed on the largest surface placed on the print bed in order to avoid printing unnecessary support material. As for the 3D design guidance, I've used the [UltiMaker Cura](https://ultimaker.com/software/ultimaker-cura/) slicer software so I could see how the model would be sliced and printed.

{% include gallery id="cura_gallery" caption="Catchcam enclosure in UltiMaker Cura slicer. Note the orientation of the top and bottom enclosure parts." %}

3D print came out quite nicely, although I encountered issues with the first print due to improper printer calibration, resulting in missing walls around cutouts. Also, the fit was rather tight, so I had to grind down the edges a bit in order to make the assembly easier.

{% include gallery id="enclosure_print_1_gallery" caption="First Catchcam enclosure 3D print." %}

The second print came out much better and the fit was still tight, but I didn't have to grind down the edges. Also, the walls around the cutouts were printed properly. Note that the screws are now on the bottom side of the enclosure.

{% include gallery id="enclosure_print_2_gallery" caption="Second Catchcam enclosure 3D print." %}

The last step of the process would be to attach four rubber feet to the bottom of the enclosure in order to prevent it from sliding off the surface. I haven't decided on the type of rubber feet yet, but I'm thinking about using self-adhesive rubber feet that are commonly used for furniture if I could find them in the right size.

{% include figure popup=true image_path="/assets/images/rubber_feet.jpg" caption="Rubber feet. Courtesy of amazon.com." %}

## Future Plans

I don't like how the Volume rotary knob doesn't stick out enough from the enclosure, so I would like to make it stick out a bit more in the future. I haven't managed to find a suitable knob with larger knob diameter and maybe a redesign of the PCB would be necessary. Maybe I can "extrude" the part of the PCB where the rotary knob is located so it sticks out more. I wouldn't want to do that, actually, because I prefer the rectangular shape of the PCB. In order to make knob adjustment easier, I've made quite a large cutout so the thumb finger can easily reach the knob.

{% include figure popup=true image_path="/assets/images/enclosure_print_1_15.jpeg" caption="Rotary knob cutout." %}

I'm thinking about spray painting the enclosure in the future in order to make it look more professional and to protect the PLA from UV light. Later, I would like to laser engrave the logo on the top part of the enclosure with the name of the project, and add labels for the LEDs and the Volume rotary knob. I presume that the laser would burn the spray paint and reveal the PLA color beneath.

## Conclusion

I'm quite happy with the enclosure design and the way it turned out. The design is simple, clean, and functional. The assembly is easy and straightforward. I'm looking forward to testing the enclosure with the final version of the PCB and making any necessary adjustments.

**Note:** If you're interested, you can pre-order a sample at [vnucec.ivan@gmail.com](mailto:vnucec.ivan@gmail.com).
{: .notice--warning}
