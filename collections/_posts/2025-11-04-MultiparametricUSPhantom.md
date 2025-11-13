---
layout: review
title: "A Novel 3-D Multiparametric Ultrasonic Phantom for Anatomy, Elasticity, Blood Flow and Tissue Orientation Imaging"
tags: Phantom Ultrasound Elastography Doppler Imaging
date: 2025-11-04
author: "Celia Mansilla & Clara Cousteix"
cite:
    authors: "Bailey Leadford, Jean-Baptiste Guillaumin, Mickaël Tanter, Jean-Francois Aubry, Beatrice Berthon"
    title:   "A Novel 3-D Multiparametric Ultrasonic Phantom for Anatomy, Elasticity, Blood Flow and Tissue Orientation Imaging"
    venue:   "Ultrasound in Medicine & Biology, 2025"
pdf: "https://www.sciencedirect.com/science/article/pii/S0301562925003011"
---

# Highlights

- **First 3D multiparametric ultrasound phantom** combining elasticity contrast, vascular flow, and tissue anisotropy in a single model.  
- **Innovative design** using magnetic orientation of scatterers to reproduce realistic tissue microstructure.  
- **Validated across multiple ultrasound modalities** (B-mode, SWE, Power Doppler, BTI) — all within the same field of view.  
- A **step toward realistic, multimodal validation tools** for next-generation clinical imaging developments.  

# Introduction

* **Multiparametric imaging** aims to image and/or measure different physiological characteristics of tissues, such as morphology and rigidity. Ultrasound (US) imaging shows strong potential for multiparametric imaging, with most applications focusing on prostate and breast cancer.  
* The development of phantoms with relevant structures is required to validate multiparametric imaging.  
* This work focuses on the design of a **multiparametric phantom** for evaluation using US imaging, combining the following modalities:  
    * **B-mode** for anatomical structure  
    * **Shear Wave Elastography (SWE)** to map local tissue stiffness  
    * **Power Doppler** to visualize blood vessels  
    * **Backscatter Tensor Imaging (BTI)** for tissue microstructure organization  
* BTI provides maps of **tissue coherence**, **tissue anisotropy**, and **tissue organization**, which can be informative about tumor invasiveness.  
* To date, there is no reported literature on phantoms simultaneously mimicking different tissue elasticities, the presence of blood vessels, and distinct scatterer organizations within the same 3D volume. This work proposes an original design for such a phantom and evaluates it using B-mode, SWE, Power Doppler, and BTI.  

# Materials and methods 

## Phantom design

The target application is breast cancer imaging. The phantom was designed as a gel matrix containing:  
* a **cylindrical rigid inclusion**, to mimic a tumor  
* a **wall-less tubing** twisting around the inclusion, made by a removed catheter, representing a blood vessel  
* **iron-particle scatterers** within a magnetic field to provide controlled tissue orientation  

As shown in the figure below, the phantom was molded in a 3D-printed box. Openings were designed for the catheter representing the blood vessel and for the mold of the rigid inclusion. After gel setting and catheter removal, double-male catheter connectors were inserted into each catheter hole from the outside of the phantom and glued in place to prevent any leakage.  

The magnetic particles embedded in the outer gel matrix were oriented using external magnets. These orientations were chosen to resemble specific fiber bundle geometries that are characteristic of the tumor microenvironment.  

![](/collections/images/20251107_Multiparametric_US_Phantom/Phantom_set_up.jpg)


## Gel preparation

The **outer gel** was prepared using 10% glycerin and 2% agar. After heating and degassing, 10% iron particles were mixed into the solution before pouring it into the mold. Once the outer gel had set, the cylindrical inclusion was removed, and the **inner gel** was prepared with the following proportions: 10% glycerin, 3% agar, and 10% iron powder. The inner gel was therefore more rigid due to the higher agar concentration.  

Once both gels were set, the catheter was removed to create the wall-less blood vessel cavity. During imaging, a blood-mimicking fluid ($$\mu = 1.7 \times 10^{-3}~\text{Pa·s}$$ and $$\rho = 1040~\text{kg/m}^3$$) was injected at a flow rate of $$0.5~\text{mL/min}$$ using a syringe.  


## US acquisition sequence

#### Materials

* Vantage Reasearch Ultrasound Platform (Verasonics)
* 15 MHz probe LA Vermon
* Probe fixed to a motor with three degrees of freedom for translation and 1 degree in rotation (needed for fiber orientation).

#### Imaging sequences

##### Shear Wave Elastography (SWE)

**Goal**: reconstruct 3D SWE map of material stiffness from shear wave speed estimation.

1. Shear waves generation: nine short focused ultrasound pulses.
2. Capture waves: using ultrafast imaging to record these shear waves with 3 titled plane waves.
3. The phantom was scanned in three different directions (0°, 45° and 90°) with a spatial resolution of 0.25 mm.
4. 3D map was reconstructed by averaging 2D maps obtained in each of the three directions.

##### Power Doppler imaging

Ultrafast Power Doppler 3D volume based on 127 2D planes in 3 orientations:
* 200 images @ FR 1 KHz
* 11 tilted PW @ 15 MHz

Power Doppler was used for 2 purposes:
1. **Blood flow data**:
- Single Value Decomposition (SVD) of 200 images.
- Remove the first five eigenvectors containing stronger signals from tissue and filter out tissue motion.
- Averaging of 3 scanning directions.

2. **Blood vessel diameter**:
- Obtain a binarized image to highlight the vessels.
- Small gaps from binarization were removed using morphological opening in Matlab.
- Bwskel function was used to obtain the centerline of the vessel.
- Vessel diameter was estimated measuring the distance between each point of the centerline and the nearest point in the vessel wall.

##### Backscatter tensor imaging (BTI)

Used to measure anisotropy and tissue orientation.

- Tomographic BTI: probe was rotated around Z-axis at steps of 10 degrees. *Interest*: capture backscattering in multiple angles and detect tissue orientation.

- At each angle the coherence factor was calculated in small blocks (local BTI):

    - high coherence: well-aligned tissue
    - low coherence: less organized tissue


# Results 

## Phantom Inspection

For the inspection of iron particle orientation, the phantom was horizontally sliced and analyzed under a microscope.  

![](/collections/images/20251107_Multiparametric_US_Phantom/Phantom_inspection.jpg)

Inspections were performed in regions containing the outer matrix, the rigid inclusion, and the wall-less tube, as shown in Figure 2:  
* **Figure 2b** shows that iron particles located far from the inclusion (and its magnets) are largely parallel to the inclusion boundary. A 2 mm-wide zone is also observed where particle organization is perturbed by the discontinuity of the magnets and the strong local magnetic field. The wall-less tube section can be seen, indicated by the black arrow.  
* In **Figure 2c**, an area close to the external magnet is presented. The local magnetic field affects the orientation of the iron particles, which are no longer parallel to the inclusion boundaries.  
* **Figure 2d** provides close-up views. The first confirms the non-parallel orientation of the particles near the external magnet, while the second shows the randomly oriented particles within the rigid inclusion, which were not exposed to a magnetic field.  

Microscopic imaging confirmed that the overall particle orientation followed the expected pattern, except at the borders of the phantom and inclusion boundaries. The wall-less vessel diameter was measured over 10 sections from different phantom slabs as $$0.98 \pm 0.13~\text{mm}.$$  

## US Acquisition Sequences

#### Shear Wave Elastography (SWE)

SWE maps were acquired in two perpendicular planes intersecting the rigid inclusion (Figure 3b). High contrast was observed in the reconstructed maps and quantified using the velocity histogram: **8.87 m/s** within the rigid inclusion versus **6.19 m/s** in the outer matrix (Figure 3d).  

![](/collections/images/20251107_Multiparametric_US_Phantom/SWE_results.jpg)



#### Power Doppler

A high contrast was obtained between the blood vessel and the background.  

- The mean Doppler intensity inside the binarized vessel was **–42.3 dB**, compared to **–78.4 dB** in the surrounding voxels, as shown in the figure below.  
- The measured blood vessel diameter was approximately **0.978 mm**, in close agreement with the real value of **1 mm**.  

![](/collections/images/20251107_Multiparametric_US_Phantom/PW_results.jpg)


#### Backscatter Tensor Imaging (BTI)

A strong agreement was observed between the BTI orientation maps and the corresponding microscopic images, confirming the expected particle alignment within the phantom.  

![](/collections/images/20251107_Multiparametric_US_Phantom/BTI_results.jpg)


#### Multiparametric View

The main objective was achieved: **3D datasets** were successfully acquired at identical locations using different US imaging sequences.  

1. **SWE and Power Doppler** (Figure 6b): The SWE threshold was set at **8.5 m/s**, highlighting the rigid inclusion in red, while the Power Doppler signal enabled clear identification of the vessel in green.  
2. **B-mode and BTI** (Figure 6c): These modalities illustrated the orientation of magnetic particles, showing **radial alignment near the inclusion boundary** that transitions to **parallel alignment** farther from the inclusion.  

![](/collections/images/20251107_Multiparametric_US_Phantom/multiparam_results.jpg)


# Discussion

The goal of this work was to design a **multiparametric phantom** enabling the acquisition of 3D maps containing information about:  

1. Echogenicity (**B-mode**)  
2. Elasticity (**SWE**)  
3. Fluid flow (**Power Doppler**)  
4. Medium orientation (**BTI**)  
5. *Local coherence and tissue anisotropy* (not within the scope of this article)  

To obtain these different image sequences, a phantom incorporating the necessary structural and physical features was developed:  
- A **cylindrical inclusion** to simulate increased rigidity  
- A **wall-less blood vessel** to assess morphology and flow  
- **Magnetic scatterers** to generate controlled orientation patterns  

The obtained results were encouraging, although several limitations were reported:  

- **Shear Wave Velocity (SWV)** maps of the outer gel were consistent with values found in the literature, indicating that the magnetic particles did **not affect shear wave estimation**.  
- The **SWV ratio** between the inclusion and the outer matrix was in line with those observed in healthy and malignant breast tissues, differing by only **12% from the true value**.  
- The **wall-less vessel technique** proved effective in generating a vessel with the desired diameter, differing by only **2.2% from the nominal value**.  
    - A potential limitation noted was the possible **increase in vessel diameter over repeated use**, which was not monitored in this study.  
- **BTI** successfully captured the **radial orientation** of the tissue around the inclusion.  
    - Some **variability in scatterer orientation** across depths was reported, attributed to the use of iron particles.  

**Comments:**  
Making the phantom more realistic would require incorporating additional cancer-related properties, such as:  
- Softer or more heterogeneous tissue regions  
- Localized variations in stiffness  
- Complex vascularization patterns  

**Future Work:**  
1. Develop a more anatomically and mechanically realistic phantom for specific clinical applications.  
2. Design and produce a range of multiparametric phantoms tailored for various imaging and diagnostic studies.  


# Conclusion

A **novel multiparametric phantom** was developed, incorporating distinct structures that enable the use of multiple ultrasound modalities within the same field of view.  

This phantom represents a **valuable tool** for the development and validation of **multiparametric ultrasound imaging protocols** and could become essential for clinical translation and training purposes.  

