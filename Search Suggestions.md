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

  // Sample list of predefined suggestions (replace this with your own data source)
  const predefinedSuggestions = [
    'Apple',
    'Banana',
    'Cherry',
    'Date',
    'Fig',
    'Grapes',
    'Kiwi',
    'Lemon',
    'Mango',
    'Orange',
  ];

  // Function to handle input change
  const handleInputChange = (e) => {
    const value = e.target.value;
    setInputValue(value);

    // If the input is empty, show all suggestions
    if (value.trim() === '') {
      setSuggestions(predefinedSuggestions);
      setIsOpen(true); // Open the dropdown when the input is focused
    } else {
      // Filter suggestions based on user input
      const filteredSuggestions = predefinedSuggestions.filter((suggestion) =>
        suggestion.toLowerCase().includes(value.toLowerCase())
      );

      setSuggestions(filteredSuggestions);
      setIsOpen(true); // Open the dropdown when there are suggestions
    }
  };

  // Function to handle suggestion click
  const handleSuggestionClick = (suggestion) => {
    setInputValue(suggestion);
    setSuggestions([]); // Clear suggestions
    setIsOpen(false); // Close the dropdown when a suggestion is clicked
  };
```

## Return
```jsx
  return (
    <div className="autocomplete">
      <div ref={inputRef}>
        <input
          type="text"
          placeholder="Type something..."
          value={inputValue}
          onChange={handleInputChange}
          onFocus={() => {
            // Show all suggestions when the input is focused
            setSuggestions(predefinedSuggestions);
            setIsOpen(true);
          }}
        />
      </div>
      {isOpen && suggestions.length > 0 && (
        <ul className="suggestions" ref={suggestionsRef}>
          {suggestions.map((suggestion, index) => (
            <li key={index} onClick={() => handleSuggestionClick(suggestion)}>
              {suggestion}
            </li>
          ))}
        </ul>
      )}
    </div>
  );
```
