# JSDetectDynamicScroll
JavaScript detect dynamic scroll it doesn't matter if the container adding new element it will automatically adjust for us!

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
      
      // check the value of current Y base on detector if
      // greater that or equalt to target elements that source of triggered!
      // Then if true ?! do set the target Element that wants to be Manipulate!
      if( window.pageYOffset >=  _targetID.bottom ) 
      { toBePurple.style.backgroundColor = 'purple'; } 
      else {
      // Else return default !  
        toBePurple.style.backgroundColor = 'yellow';
      }
    };
  
 </script>
</body>
</html>
```
