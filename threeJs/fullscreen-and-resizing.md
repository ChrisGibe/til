# Fullscreen and resizing

Our canvas currently has a fixed resolution. You don't necessarily need your WebGL to fit the whole screen, but if you want an immersive experience, it might be better.

```
/**
 * Sizes
 */
const sizes = {
    width: window.innerWidth,
    height: window.innerHeight
}

window.addEventListener('resize', () => {

    // Update sizes
    sizes.width = window.innerWidth
    sizes.height = window.innerHeight

    // Update Camera
    camera.aspect = sizes.width / sizes.height
    camera.updateProjectionMatrix()

    // Update Renderer
    renderer.setSize(sizes.width, sizes.height)
    renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2))
})

window.addEventListener('dblclick', () => {
    const fullscreenElement = document.fullscreenElement || document.webkitFullscreenElement

    if(!fullscreenElement) {
        if(canvas.requestFullscreen) {
            canvas.requestFullscreen()
        }else if(canvas.webkitRequestFullscreen){ // For Safari
            canvas.webkitRequestFullscreen()
        }
    }else {
        if(document.exitFullscreen) {
            document.exitFullscreen()
        }else if(document.webkitExitFullscreen) { // For Safari
            document.webkitExitFullscreen()
        }
        
    }
    
})
```