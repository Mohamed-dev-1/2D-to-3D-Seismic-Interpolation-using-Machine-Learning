**Overview :**

This project uses machine learning to reconstruct a continuous 3D seismic volume from a set of sparse 2D seismic lines. 
Seismic surveys often provide 2D cross-sections (inlines, crosslines, random lines) with gaps between them due to acquisition cost and coverage limits. 
Since subsurface geology varies smoothly and continuously in space, a neural network can learn the spatial relationship between known lines and predict the missing sections between them, effectively interpolating a full 3D volume from partial 2D data.

**Simply :**

* We have seismic scans of underground rock with gaps between them, and we're building an machine learning model that fills in those gaps, turning a bunch of separate 2D slices into one complete 3D picture of the underground.

---

**Input Data :**

* 2D seismic sections in SEGY format (inlines, crosslines, random lines)
* ASCII geometry file (inline, crossline, CMP X-coordinate, CMP Y-coordinate)

---

**Pipeline**
- Data inspection : read and visualize SEGY lines, review geometry file, identify line spacing
- Training sample preparation : use pairs of known neighboring lines as inputs, known intermediate lines as targets
- Model training : train a neural network to reconstruct intermediate seismic sections from neighboring sections
- Validation : hold out known intermediate lines, compare predicted vs. actual to evaluate accuracy
- Full-volume interpolation : apply the trained model across the geometry to generate all missing sections
- Export : assemble and save the reconstructed 3D volume as a SEGY file

---

**Output :**

A continuous 3D SEGY seismic volume reconstructed from the original sparse 2D lines.
