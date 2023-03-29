# JSDetectDynamicScroll
JavaScript detect dynamic scroll it doesn't matter if the container adding new element it will automatically adjust for us!
<br />
<br /> Learn About Browser document detector : https://github.com/nielsoffice/JSDOMRect

```HTML
<html>
<head></head>
<style>
#elemTarget,
#elemTarget2,
#elemTargeta {
  width: 100%;
  height: 200px;  
}

#elemTargeta,
#elemTarget {
  background-color: red;     
}

#elemTarget2 {
  background-color: rgb(255, 187, 0);     
}

</style>
<body id="app-id">
<!-- 
  If ever there will additional content or div tag here this detection will
  dynamically adjust for us!
<br />
<br />
<br />
<br /><br />
<br /><br />
<br /><br />
<br /><br />
<br /> 
-->
<div id="elemTargeta">
  <p>Demo Content...</p>
</div>
<div id="elemTarget1">
  <p>Demo Content...</p>
</div>
<div id="elemTarget2">
  <p>Demo Content...</p>
</div>
<div id="elemTargetb">
  <p>Demo Content...</p>
</div>
<div id="elemTarget1">
  <p>Demo Content...</p>
</div>
<div id="elemTarget2">
  <p>Demo Content...</p>
</div>
<div id="elemTarget">
  <p>Demo Content...</p>
</div>
<div id="elemTarget1">
  <p>Demo Content...</p>
</div>
<div id="elemTarget2">
  <p>Demo Content...</p>
</div>
<div id="elemTargeta2">
  <p>Demo Content...</p>
</div>
<div id="elemTarget1">
  <p>Demo Content...</p>
</div>
<div id="elemTarget2">
  <p>Demo Content...</p>
</div>
<div id="elemTargetb">
  <p>Demo Content...</p>
</div>
<div id="elemTarget1">
  <p>Demo Content...</p>
</div>
<div id="elemTarget2">
  <p>Demo Content...</p>
</div>

<script id="app-data">
  
    // Target the elem which cuz of trigger of other to be manipulated
    // ex. the next div will turn into purple!
    let targetID  = document.getElementById('elemTargeta'); 
    // Get the top or bottom properties for the target element that once
    // detector reached it will triggered
    // console.log( targetID.getBoundingClientRect() );
    // Reference: https://github.com/nielsoffice/JSDOMRect
    let _targetID = targetID.getBoundingClientRect();  
     
    // Select the element that you want to be manipulated once
    // target element are reached or detected!
    let toBePurple  = document.getElementById('elemTarget2');
   
    // Event use "onscroll" function that not affect the current value of
    // other element while scrolling otherwise use EventListener
    // ex. elem.addEventListener('scroll', function() { ... });
    // to get dynamic update value from any documents elements
    onscroll = (event) => {
      
      // IF BASE ON | let baseOnElemHeight = (_targetID.height / 2) + _targetID.y  ;
      // check the value of current Y base on detector if
      // greater that or equal to target elements that source of triggered!
      // Then if true ?! do set the target Element that wants to be Manipulate!
      if( window.pageYOffset >=  _targetID.bottom ) // >= baseOnElemHeight
      { toBePurple.style.backgroundColor = 'purple'; } 
      else {
      // Else return default !  
        toBePurple.style.backgroundColor = 'yellow';
      }
    };
    
    // Default Refresh scroll back to top!
    window.onbeforeunload = function () {
      window.scrollTo(0, 0);
    }
  
 </script>
</body>
</html>
```

<br />USING Intersection_Observer_API JS | This approach detect begin from bottom, as the "getBoundingClientRect()" read from top scrolling down, The "Intersection_Observer_API" will read bottom scrolling down.
<br />In addition, Keep in mind Any element that not yet showed in document screen or viewport from the bottom through scrolling down the new element or html tag will detect with this approach, While any element that will hide to top through scrolling down will detect with "getBoundingClientRect()" method.
<br />
<br />Intersect while hiding the content : getBoundingClientRect() | scrolling down
<br />Intersect while showing the content from bottom : Intersection_Observer_API | scrolling down

```HTML
<html><head><style>
  #elemTargeta,
  #elemTargetb,
  #elemTargetc,
  #elemTargetd,
  #elemTargete,
  #elemTargetf,
  #elemTargetg {
    width: 100%;
    height: 300px;  
  }
  
  #elemTargeta,
  #elemTargetc,
  #elemTargete, 
  #elemTargetg {
    background-color: red;     
  }
  
  #elemTargetb,
  #elemTargetd,
  #elemTargetf {
    background-color: rgb(255, 187, 0);     
  }
  
  </style></head>
  
  <body id="app-id">
  
  <div id="elemTargeta" class="cons">
    <p>Demo Content...</p>
  </div>
  
  <div id="elemTargetb" class="cons">
    <p>Demo Content...</p>
  </div>
  
  
  <div id="elemTargetc" class="cons">
    <p>Demo Content...</p>
  </div>
  <div id="elemTargetd" class="cons">
    <p>Demo Content...</p>
  </div>
  
  <div id="elemTargete" class="cons">
    <p>Demo Content...</p>
  </div>
  
  
  <div id="elemTargetf" class="cons">
    <p>Demo Content...</p>
  </div>
  
  
  <div id="elemTargetg">
    <p>Demo Content...</p>
  </div>
  
  <script id="app-data">
    
    // Ref.: https://developer.mozilla.org/en-US/docs/Web/API/Intersection_Observer_API
    const allElem = document.querySelectorAll('.cons');
  
    const revealed = function(e,o) {
  
      const [entry] = e;
      console.log(entry);
      /* do something */
      // ex. if( !entry.isIntersect) { return ... do something! }
      // Which means if intersect is false;
  
    }
   
    // threshold: 0.0 to 1.0 stand for percentage that intersect to the element
    // ex. 1.0 means 100% as long as the detector are within 100% or 1.0 it will intersect
    // to the target element
    // @method revealed is a callback function
    const sectionObserver = new IntersectionObserver(
      revealed, {
        root: null,
        threshold: 0, // 0 means 0% detect each element as long as detector detected it then out!.
      }
    );
    
    // Then isIntersect return FALSE as the recent element not detected as the new element html tag dectected it will return TRUE for isIntersect from "0" base !
    
    // loop if you want to check to intersect more than 1 element
    allElem.forEach(function(v, index) { sectionObserver.observe(v); });
  
    window.onbeforeunload = function () {
       window.scrollTo(0, 0);
    }
    
   </script>
  
  </body></html>
```
