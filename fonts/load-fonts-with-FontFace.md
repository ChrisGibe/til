# Load fonts with FontFace

Sometimes it is necessary to wait for the fonts to be loaded before launching your web page, it is possible to do this via this small function that I created, and to insert callbacks (or not, this is not not obligatory) in order to execute certain functions such as for example launching a SplitText with gsap, the usual problems linked to this method are thus avoided

```

export const loadFonts = async (fonts, callbacks = []) => {
    try {
      
        // Creation of promises for each font
        const fontPromises = fonts.map(({ name, url, weight = 'normal', style = 'normal' }) => {
          const fontFace = new FontFace(name, `url(${url})`, { weight: weight, style: style });
          return fontFace.load();
        });
    
        // Wait until all the fonts are loaded
        const loadedFonts = await Promise.all(fontPromises);
    
        // Add each font loaded to the document
        loadedFonts.forEach(font => {
          document.fonts.add(font);
        });
    
        // Wait until all the fonts are ready in FontFaceSet
        await document.fonts.ready;
        console.log('All the fonts are ready');

        // Launch all the callbacks
        if (Array.isArray(callbacks)) {
          callbacks.forEach(callback => {
            if (typeof callback === 'function') {
              callback();
            }
          });
        }
      } catch (error) {
        console.error('Error loading fonts:', error);
      }
};

```