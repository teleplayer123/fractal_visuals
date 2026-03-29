⏺ This program creates a psychedelic fractal visualization using WGPU (WebGPU) and WGSL shaders.
                                  
  1. It initializes a window using winit for rendering graphics                           
  2. Sets up a WGPU graphics context with high-performance adapter
  3. Creates a shader module from a WGSL file (fractal.wgsl)                                                                                            
  4. Defines uniform variables for screen size, time, and zoom parameters
  5. Creates a uniform buffer to pass these values to the shader                                                                                        
  6. Sets up a bind group layout and bind group for shader uniforms
  7. Creates a render pipeline using the shader
  8. Runs an event loop that:
    - Updates time and zoom values periodically (zoom doubles every 2 seconds)
    - Writes updated uniforms to the buffer
    - Renders a full-screen triangle using the fractal shader
    - Presents the rendered frame

  The program implements a dynamic zoom effect that cycles through powers of 2 (from 1 to 2^18) to create an animated fractal visualization. The actual
  fractal rendering logic is in the separate fractal.wgsl file, which is included as source code.

  The key behavior is:
  - Time-based animation: uniforms.time updates each frame
  - Zoom cycling: uniforms.zoom doubles every 2 seconds, resets after reaching 2^18
  - Continuous rendering loop that redraws the fractal with updated parameters

⏺ This WGSL shader file implements a Julia set fractal visualization with psychedelic coloring and animated zoom effects. Here's what it does:
                                  
  1. Uniforms Structure: Defines screen size, time, and zoom parameters that are passed from Rust code                                                  
  2. Vertex Shader (vs_main):
    - Creates a full-screen triangle using vertex index manipulation                                                                                    
    - Maps vertex indices to screen coordinates (-1 to 1 range)                                                                                         
  3. Fragment Shader (fs_main):                                                                                                                         
    - Takes the vertex position and converts it to normalized screen coordinates                                                                        
    - Applies zoom transformation to these coordinates                                                                                                  
    - Uses a specific Julia set constant with time-varying perturbations for maximum complexity                                                         
    - Implements iterative complex math: z = z² + c (standard Julia set formula)                                                                        
    - Uses smooth coloring algorithm for better visual quality                                                                                          
    - Applies high-frequency psychedelic colors based on iteration count and time                                                                       
    - Returns the final color value                                                                                                                     
                                                                                                                                                        
  The program creates a mesmerizing, animated fractal visualization where:                                                                              
  - The Julia set constant is slowly oscillating over time for dynamic effects                                                                          
  - Zoom increases exponentially (doubles every 2 seconds) up to a maximum of 1024x                                                                     
  - Colors cycle through sine waves for psychedelic visual effects                 
  - The "Infinite Spiral" coordinate provides a deep zoom point that creates interesting patterns 