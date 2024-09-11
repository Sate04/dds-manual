<style>
* {box-sizing:border-box}

/* Slideshow container */
.slideshow-container {
  max-width: 1000px;
  position: relative;
  margin: auto;
}

/* Hide the images by default */
.mySlides {
  display: none;
}
#slide1 {display:block}

/* Next & previous buttons */
.prev, .next {
  cursor: pointer;
  position: absolute;
  top: 250px;
  width: auto;
  margin-top: -22px;
  padding: 16px;
  color: white;
  font-weight: bold;
  font-size: 18px;
  transition: 0.6s ease;
  border-radius: 3px 3px 3px 3px;
  user-select: none;
}

/* Position the "next button" to the right */
.next {
  right: 0;
}

/* On hover, add a black background color with a little bit see-through */
.prev:hover, .next:hover {
  background-color: rgba(0,0,0,0.6);
}

/* Caption text */
.text {
  color: #f2f2f2;
  font-size: 15px;
  padding: 8px 12px;
  position: absolute;
  bottom: 8px;
  width: 100%;
  text-align: center;
}

/* Number text (1/3 etc) */
.numbertext {
  color: #f2f2f2;
  font-size: 12px;
  padding: 8px 12px;
  position: absolute;
  top: 0;
}

/* The dots/bullets/indicators */
.dot {
  cursor: pointer;
  height: 15px;
  width: 15px;
  margin: 0 2px;
  background-color: #bbb;
  border-radius: 50%;
  display: inline-block;
  transition: background-color 0.6s ease;
}

.active, .dot:hover {
  background-color: #717171;
}

/* Fading animation */
.fade {
  animation-name: fade;
  animation-duration: 0.25s;
}

@keyframes fade {
  from {opacity: .4}
  to {opacity: 1}
}
</style>

# 1B: Power Transmissions

## Introduction

So far the models you have created are all structural components, but this is only half of what makes up a robot. In order to make our robots move and score, motors that generate rotational motion are typically utilized. In Stage 1B, you'll be introduced to modeling basic *power transmissions*. Power transmissions include the motors, bearings, shafts, gears, belts, and chains that are used to transform rotational motion from a motor to do just about anything. 

In this stage, you'll focus on the fundamentals of power transmissions, with an emphasis on how to model them in CAD. The process of selecting motors and calculating power transmission ratios will be explored later in Stage 2 of the guide with multiple different mechanisms.

### Examples

Take a look below at some examples of different types of power transmissions found in robots.

!!! Example "Examples of Power Transmissions in Robots"
    <center>**Power Transmission Examples**</center>
    <!-- Slideshow container -->
      <div class="slideshow-container">
      <!-- Full-width images with number and caption text -->
      <div id="slide1" class="mySlides fade">
          <figure>
              <img src="/img/learning-course/stage1b/examples/intakeRollers.webp" style="width:80%">
              <figcaption> Belt and gear power transmission to spin intake rollers. </figcaption>
          </figure>
      </div>
      <div class="mySlides fade">
          <figure>
              <img src="/img/learning-course/stage1b/examples/intakePivot.webp" style="width:80%">
              <figcaption> Gear and chain power transmission to pivot the intake. </figcaption>
          </figure>
      </div>
      <div class="mySlides fade">
          <figure>
              <img src="/img/learning-course/stage1b/examples/shooter.webp" style="width:80%">
              <figcaption> Belt and gear power transmission to spin shooter wheels.</figcaption>
          </figure>
      </div>
      <div class="mySlides fade">
          <figure>
              <img src="/img/learning-course/stage1b/examples/ampArm.webp" style="width:60%">
              <figcaption> Gear and chain power transmission to rotate a small arm. </figcaption>
          </figure>
      </div>
      <div class="mySlides fade">
          <figure>
              <img src="/img/learning-course/stage1b/examples/armGearbox.webp" style="width:75%">
              <figcaption> Gear and chain power transmission to rotate a large arm.</figcaption>
          </figure>
      </div>
      <!-- Next and previous buttons -->
      <button class="prev" onclick="plusSlides(-1,0)" style="background-color: #000; color: #fff;">&#10094;</button>
      <button class="next" onclick="plusSlides(1,0)" style="background-color: #000; color: #fff;">&#10095;</button>
      <!-- The dots/circles -->
      <div class="dotsContainer" style="text-align:center">
      <!-- Dots will be generated here -->
      </div>
    </div>

In this stage, there are exercises designed to practice modeling simple power transmissions in the form of stand alone gearboxes. In stage 2, you will begin to model power transmissions integrated within mechanisms.

<br>

<!-- ------------------DO NOT TOUCH ANYTHING BELOW HERE------------------ -->

<script>
// Initialize slide index for each slideshow
let slideIndices = [];

let slideshows = document.getElementsByClassName("slideshow-container");
  for (let no = 0; no < slideshows.length; no++) {
    slideIndices[no] = 1;
    let dotsContainer = slideshows[no].getElementsByClassName("dotsContainer")[0];
    let slides = slideshows[no].getElementsByClassName("mySlides");
    for (let i = 0; i < slides.length; i++) {
      let dot = document.createElement("span");
      dot.className = "dot";
      dot.onclick = function() { currentSlide(i+1, no); };
      dotsContainer.appendChild(dot);
    }
    showSlides(1, no);
  }

// Next/previous controls
function plusSlides(n, no) {
  showSlides(slideIndices[no] += n, no);
}

// Thumbnail image controls
function currentSlide(n, no) {
  showSlides(slideIndices[no] = n, no);
}

function showSlides(n, no) {
  let i;
  let x = document.getElementsByClassName("slideshow-container")[no].getElementsByClassName("mySlides");
  let dots = document.getElementsByClassName("slideshow-container")[no].getElementsByClassName("dot");
  if (n > x.length) {slideIndices[no] = 1}    
  if (n < 1) {slideIndices[no] = x.length}
  for (i = 0; i < x.length; i++) {
    x[i].style.display = "none";  
  }
  for (i = 0; i < dots.length; i++) {
    dots[i].className = dots[i].className.replace(" active", "");
  }
  x[slideIndices[no]-1].style.display = "block";  
  dots[slideIndices[no]-1].className += " active";
}

</script>