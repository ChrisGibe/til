# Add a loader based on the images, scripts and styles of the page


```
class Loader {
  constructor() {
    this.totalElements = document.querySelectorAll('img, script, link[rel="stylesheet"]').length;
    this.htmlToUpdate = document.getElementById('your-html-element-to-update')
    this.loadedElements = 0;
    this.initLoader();
  }

  calculateOverallLoadPercentage(loadedCount, totalCount) {
    const percentage = (loadedCount / totalCount) * 100;
    return Math.min(Math.max(percentage, 0), 100);
  }

  updateLoadPercentage() {
    const loadPercentage = this.calculateOverallLoadPercentage(this.loadedElements, this.totalElements);
    this.htmlToUpdate.innerHTML = loadPercentage.toFixed(0)
  }

  initLoader() {
    document.querySelectorAll('img, script, link[rel="stylesheet"]').forEach((element) => {
      element.addEventListener("load", () => {
        this.loadedElements++;
        this.updateLoadPercentage();
      });

      element.addEventListener("error", () => {
        this.loadedElements++;
        this.updateLoadPercentage();
      });
    });

    this.updateLoadPercentage();

    window.addEventListener("load", () => {
      this.loadedElements = this.totalElements;
      this.updateLoadPercentage();
      console.log("Tout est chargé !", this.loadedElements);
    });
  }
}
```