Basic THREE.js Controls for the Leap

Right now, only two controls:
	
	- If there is one pointable, move around according to its position in 3D leap space
	
	- If there are two pointables, lock the position of the camera,
		and rotate based on the first pointables X and Y position
		
		
	To use this script, simply make sure 
		- that you call it in the html, 
		- initialize your THREE scene,
		- add the rendering function to the initLeap() function, 
			shown at the bottom of this page
		- call initLeap() to start the scene rendering!
