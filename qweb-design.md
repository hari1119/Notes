### Q-Web Custom Design Template 

# Pages
Cross-page element -> This will be in same for all the pagres **Ex.** header and footer <br/>
Uniqu element -> This will only related to a specific page.**Ex.** main

```
<div id="wrapwrap">
   <header/>
      <main>
         <div id="wrap" class="oe_structure">
            <!-- Page Content -->
         </div>
      </main>
   <footer/>
</div>
```
# Background

## colors

##### Ex. Path -> website_airproof/static/src/scss/primary_variables.scss
```
$o-color-palettes: map-merge($o-color-palettes,
   (
      'airproof': (
         'o-cc1-bg':                     'o-color-5',
         'o-cc5-bg':                     'o-color-1',
      ),
    )
);
```
## Image/pattern

```
$o-website-values-palettes: (
   (
      'body-image': '/website_airproof/static/src/img/background-lines.svg',
      'body-image-type': 'image' or 'pattern'
   )
);
```









