<script lang="ts">
    import { onMount, onDestroy } from 'svelte';
  
    let customCursor: HTMLDivElement;
  
    onMount(() => {
      // Set initial cursor position
      let cursorX = window.innerWidth / 2;
      let cursorY = window.innerHeight / 2;
  
      // Define the speed (lower values mean slower tracking)
      const trackingSpeed = 0.03;
  
      // Variables to store the target position
      let targetX = cursorX;
      let targetY = cursorY;
  
      // Function to update cursor position
      function updateCursorPosition() {
        // Calculate the distance to the target position
        const deltaX = targetX - cursorX;
        const deltaY = targetY - cursorY;
  
        // Update the cursor position gradually
        cursorX += deltaX * trackingSpeed;
        cursorY += deltaY * trackingSpeed;
  
        // Apply the cursor position
        if (customCursor) {
          customCursor.style.left = `${cursorX}px`;
          customCursor.style.top = `${cursorY}px`;
        }
  
        // Request another animation frame for continuous tracking
        requestAnimationFrame(updateCursorPosition);
      }
  
      // Function to update target position on mouse move
      function onMouseMove(e: MouseEvent) {
        targetX = e.clientX;
        targetY = e.clientY;
      }
  
      // Listen for mousemove events on the document
      document.addEventListener('mousemove', onMouseMove);
  
      // Start the continuous animation loop
      requestAnimationFrame(updateCursorPosition);
  
      return () => {
        // Cleanup event listener on component unmount
        document.removeEventListener('mousemove', onMouseMove);
      };
    });
  </script>
  
  <style>
    /* Style for the custom cursor */
    #custom-cursor {
      width: 200px;
      height: 200px;
      background-color: pink;
      position: fixed;
      pointer-events: none; /* Ensure it doesn't interfere with other elements */
      mix-blend-mode: difference; /* Apply a blending mode for the "red blur" effect */
      filter: blur(150px); /* Apply a larger blur effect */
      opacity: 0.5; /* Adjust opacity for a pronounced fade effect */
      animation: jiggleCursor 0.5s alternate infinite; /* Add jiggling animation */
    }
  </style>
  
  <div id="custom-cursor" bind:this={customCursor}></div>
  