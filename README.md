# EX05_image-carousel-in-react

#### NAME: YUVARANI T
#### REG. NO: 212222110057

#### Date:

### AIM:
To create a Image Carousel using React

### ALGORITHM:

#### STEP 1 Initial Setup:
Input: A list of images to display in the carousel.
Output: A component displaying the images with navigation controls (e.g., next/previous buttons).

#### Step 2 State Management:
Use a state variable (currentIndex) to track the index of the current image displayed.
The carousel starts with the first image, so initialize currentIndex to 0.

#### Step 3 Navigation Controls:
Next Image: When the "Next" button is clicked, increment currentIndex.
If currentIndex is at the end of the image list (last image), loop back to the first image using modulo: currentIndex = (currentIndex + 1) % images.length;
Previous Image: When the "Previous" button is clicked, decrement currentIndex.
If currentIndex is at the beginning (first image), loop back to the last image: currentIndex = (currentIndex - 1 + images.length) % images.length;

#### Step 4 Displaying the Image:
The currentIndex determines which image is displayed.
Using the currentIndex, display the corresponding image from the images list.

#### Step 5 Auto-Rotation:
Set an interval to automatically change the image after a set amount of time (e.g., 3 seconds).
Use setInterval to call the nextImage() function at regular intervals.
Clean up the interval when the component unmounts using clearInterval to prevent memory leaks.

### PROGRAM:
App.jsx
```
import React, { useState, useEffect } from 'react';

import img1 from './assets/img1.jpg';
import img2 from './assets/img2.jpg';
import img3 from './assets/img3.jpg';

const images = [img1, img2, img3];

function App() {
  const [currentIndex, setCurrentIndex] = useState(0);

  const nextImage = () => {
    setCurrentIndex((currentIndex + 1) % images.length);
  };

  const prevImage = () => {
    setCurrentIndex((currentIndex - 1 + images.length) % images.length);
  };

  useEffect(() => {
    const intervalId = setInterval(() => {
      nextImage();
    }, 3000);

    return () => clearInterval(intervalId);
  }, [currentIndex]);

  return (
    <div style={{ textAlign: 'center', maxWidth: 600, margin: 'auto' }}>
      <h2>React Image Carousel</h2>
      <div style={{ position: 'relative' }}>
        <img
          src={images[currentIndex]}
          alt={`Slide ${currentIndex}`}
          style={{ width: '100%', height: 'auto', borderRadius: 8 }}
        />
        <button
          onClick={prevImage}
          style={{
            position: 'absolute',
            top: '50%',
            left: 10,
            transform: 'translateY(-50%)',
            fontSize: '1.5rem',
            backgroundColor: 'rgba(255,255,255,0.7)',
            border: 'none',
            borderRadius: '50%',
            cursor: 'pointer',
            padding: '0.5rem 1rem',
          }}
          aria-label="Previous Image"
        >
          &#8592;
        </button>
        <button
          onClick={nextImage}
          style={{
            position: 'absolute',
            top: '50%',
            right: 10,
            transform: 'translateY(-50%)',
            fontSize: '1.5rem',
            backgroundColor: 'rgba(255,255,255,0.7)',
            border: 'none',
            borderRadius: '50%',
            cursor: 'pointer',
            padding: '0.5rem 1rem',
          }}
          aria-label="Next Image"
        >
          &#8594;
        </button>
      </div>
      <p>
        Image {currentIndex + 1} of {images.length}
      </p>
    </div>
  );
}

export default App;
```
### OUTPUT:
![image](https://github.com/user-attachments/assets/50ac2af2-f637-4808-89e2-f2b6b04f8b17)
![image](https://github.com/user-attachments/assets/f94d7517-9ef1-450d-a8b0-75966541aae5)
![image](https://github.com/user-attachments/assets/aa9a9669-f587-4e8e-abf5-c28cb5fd2c5c)

### RESULT:
The program for creating Image Carousel using React is executed successfully.
