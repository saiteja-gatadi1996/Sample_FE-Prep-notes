
## Progressive Images in React
- refers to a **technique aimed at improving user experience during image loading.**
- The concept involves **initially displaying a low-quality version of an image** (often significantly smaller in file size), and then seamlessly <ins>***replacing it with the high-quality, full-size image once it's fully loaded***</ins>. 
- This approach can significantly enhance the perceived load time and smoothness of a webpage, especially on slower internet connections.

```css
/* App.css */
body {
  padding: 10px;
}

.loading {
  filter: blur(10px); /* applies a blur effect to the placeholder image, making it look out of focus. This is often used to make the low-quality aspect of the placeholder less noticeable. */
}

.loaded {
  /* removes the blur effect from the image once the high-quality version is loaded and applies a transition effect to the filter change. The transition: filter 0.5s linear; part means that the change in the filter (from blurred to un-blurred) will occur over 0.5 seconds in a linear fashion, creating a smooth visual transition. */
  filter: blur(0px);
  transition: filter 0.5s linear;
}
```

```js
//App.js
import './App.css';
import ProgressiveImage from './ProgressiveImage';

import largeImg from './images/large.jpg';
import tinyImg from './images/tiny.jpg';

function App() {
  return (
    <>
      <h1>Progressive Image</h1>
      <ProgressiveImage
        src={largeImg}
        placeholderImg={tinyImg}
        height={'450'}
        width={'450'}
      />
    </>
  );
}

export default App;
```

```js
//ProgressiveImage.js
import { useState, useEffect } from 'react';
import PropTypes from 'prop-types'; // Import PropTypes for props validation

const ProgressiveImage = (props) => {
  const { alt, height, width, placeholderImg, src } = props;
  const [imgSrc, setSrc] = useState(placeholderImg || src);
  const [loadError, setLoadError] = useState(false);

  const customClass =
    placeholderImg && imgSrc === placeholderImg ? 'loading' : 'loaded';

  useEffect(() => {
    const img = new Image();
    img.src = src;

    const handleLoad = () => {
      setSrc(src);
    };

    const handleError = () => {
      setLoadError(true);
    };

    //The line img.onload = handleLoad; assigns the handleLoad function as an event handler for the load event of the Image object (img). This means that handleLoad will be called automatically by the browser once the image has successfully loaded.
    img.onload = handleLoad;
    img.onerror = handleError;

    return () => {
      img.onload = null; // Clean up: remove onload listener
      img.onerror = null; // Clean up: remove onerror listener
    };
  }, [src]);

  return (
    <img
      src={loadError ? placeholderImg : imgSrc} // Fallback to placeholderImg on error
      className={customClass}
      alt={alt || 'Image'} // Providing a default alt text if none is provided
      height={height}
      width={width}
    />
  );
};

// PropTypes validation
ProgressiveImage.propTypes = {
  alt: PropTypes.string,
  height: PropTypes.string.isRequired,
  width: PropTypes.string.isRequired,
  placeholderImg: PropTypes.string.isRequired,
  src: PropTypes.string.isRequired,
};

export default ProgressiveImage;
```
