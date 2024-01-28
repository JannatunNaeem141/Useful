# Scroll To Top
In case of long size webpage there is an issue we face that when we scroll down and then waht to back at top we had to scroll back to top. For that we have a solution. We can have a Sroll to Top button that will take us to the top of the website. This is how we can make this with a simple function. We can style this any way we want.

## Technologies
- ReactJS/NextJS
- TailwindCSS
- React Icons

## Import: 
```jsx
  import React, { useEffect, useState } from 'react';
  import { FaArrowUpLong } from "react-icons/fa6";
```

### In Function :
```jsx
  const [showScroll, setShowScroll] = useState(false);

    useEffect(() => {
        window.addEventListener("scroll", () => {
        if (window.pageYOffset > 100) {
            setShowScroll(true);
        } else {
            setShowScroll(false);
        }
        });
    }, []);


    const scrollTop = () => {
        window.scrollTo({ top: 0, behavior: "smooth" });
    };
```

### In Return :
```jsx
  return (
    <div>
        <div className={`fixed bottom-10 right-0 p-6 ${showScroll ? "" : "hidden"}`}>
            <div onClick={scrollTop} className="text-primary cursor-pointer bg-blue-100 hover:bg-blue-200 transition-all text-white font-bold p-3 rounded-full">
                <FaArrowUpLong className='text-lg text-blue-700' />
            </div>
        </div>
    </div>
  )
```
