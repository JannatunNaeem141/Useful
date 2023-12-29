# Search Suggestions

## Import 
```jsx
  import React, { useState, useRef, useEffect } from 'react';
```

## Functions
```jsx
  const [inputValue, setInputValue] = useState('');
  const [suggestions, setSuggestions] = useState([]);
  const [isOpen, setIsOpen] = useState(false);

  const inputRef = useRef(null);
  const suggestionsRef = useRef(null);

  useEffect(() => {
    // Event listener to close the dropdown when clicking outside
    const handleOutsideClick = (e) => {
      if (
        inputRef.current &&
        !inputRef.current.contains(e.target) &&
        suggestionsRef.current &&
        !suggestionsRef.current.contains(e.target)
      ) {
        setIsOpen(false);
      }
    };

    // Attach the event listener when the dropdown is open
    if (isOpen) {
      document.addEventListener('mousedown', handleOutsideClick);
    } else {
      // Remove the event listener when the dropdown is closed
      document.removeEventListener('mousedown', handleOutsideClick);
    }

    // Clean up the event listener when the component unmounts
    return () => {
      document.removeEventListener('mousedown', handleOutsideClick);
    };
  }, [isOpen]);
```
