###An <a href="openleap.org">OpenLeap</a> project started by @Cabbibo.

#Basic three.js Fly controls for the Leap, based off three.js FlyControls


  Control Scheme:
  
  - Hold hand out with fingers out to fly, 
  - Close hand to stop movement but look around
  - Point with hand to determine direction
  - Move hand in x / y to also determine direction 
  - Move hand in z to determine flight speed

  Parameters are as follows:

  - rollSpeed: Speed at which camera rolls with hand
  - lookSpeed: Speed at which camera looks
  - movementSpeed: Speed at which camera moves

  - directionFactor: tells you how much pointing determines direction
  - positionFactor: tells you how much position determines direction
  
  - weakDampening: how quickly movement returns to rest ( WEAK: Fingers extended )
  - strongDampening: how quickly movement returns to rest ( STRONG: Fingers closed )


  Usage:

  Include the Neccesary Scripts:

  ```html
    <!-- LEAP SCRIPT -->
    <script src="lib/leap-0.4.3.js"></script>
    
    <!-- LEAP CONTROL -->
    <script src="LeapControls.js"></script>
  ```

  In your initialization function, initialize the camera, and controller:

  '''javascript

      /*
         
         ADD THREE Camera

      */

      camera = new THREE.PerspectiveCamera(70,window.innerWidth/window.innerHeight,1,3000)
      camera.position.z = 1000;
      
      
      
      /*
      
        ADD LEAP CONTROLLER

      */

      controller = new Leap.Controller();
      controller.connect();

  '''

  Create your camera controls by passing in the camera and controller you want to use. If you want to change any parameters, do so here:
  

  '''html
      /*

         ADD LEAP CAMERA CONTROLS

      */
      controls = new THREE.LeapFlyControls( camera , controller );

      // API
      controls.rollSpeed        = .005;
      controls.lookSpeed        = .018;
      controls.movementSpeed    = .10;

      controls.directionFactor  = .01;
      controls.positionFactor   = .01;

      controls.weakDampening    = .99;
      controls.strongDampening  = .90;
      controls.dampening        = controls.weakDampening;
  
  '''

  Lastly, make sure to update your controls in the animate loop:

  '''html

    function animate() {
                  
        requestAnimationFrame( animate );
        controls.update();
        render();
        
    }

  '''

  This should get you rolling!
