## 3D model website development

With the help of ```<model-viewer>``` we can able to display the 3D model in the website.

- [model-viewer official site](https://modelviewer.dev/)
- [model-viewer docs](https://modelviewer.dev/examples/loading/index.html)
- [Docs](https://web.dev/articles/model-viewer)

```
<script type="module" src="https://ajax.googleapis.com/ajax/libs/model-viewer/3.5.0/model-viewer.min.js"></script>

<model-viewer autoplay="1" class="model-3d" animation-name="Running"  alt="Trinode Pointers" 
            src="https://cdn.jsdelivr.net/gh/hari1119/TrinodePointers@Master/3d-models/earth_our_fragile_home.glb"
            shadow-intensity="1"  ar='1' ar-modes="webxr scene-viewer" 
            camera-controls="1" scale="0.2 0.2 0.2"></model-viewer>

```
Download 3D models here for free -> [Free 3D-Models](https://sketchfab.com/features/free-3d-models)
Interactive 3D models -> [spline](https://community.spline.design/)

In the above example ```src``` part, i push the 3D model file in the git hub,then using the github link i convert it a jsdelivr link to improve performance.

- [Convet the Git link to Jsdelivr format](https://www.jsdelivr.com/github)

After convetion if we wanna check that working nature, use the below site to check that.
- [codepen.io](https://codepen.io/pen/)

**Final output:**
![image](https://github.com/user-attachments/assets/cb995d4b-1acd-45e8-b251-4567be9328eb)



