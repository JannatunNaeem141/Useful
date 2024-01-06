# Custom Accordion
This is a custom accordion for frequently asked questions.

## Technologies
- ReactJS/NextJS
- TailwindCSS & CSS
- React Icons

## Import
```jsx
  import { HiMinus, HiPlus } from 'react-icons/hi';
```

## Functions
```jsx
    const [activeIndex, setActiveIndex] = useState(null);

  const handleClick = (index) => {
    if (index === activeIndex) {
      setActiveIndex(null);
    } else {
      setActiveIndex(index);
    }
  };

  const questions = [
    {
      question: 'What is React?',
      answer:
        'React is a JavaScript library for building user interfaces. It allows developers to create reusable UI components and manage the state of their application efficiently.'
    },
    {
      question: 'What is Tailwind CSS?',
      answer:
        'Tailwind CSS is a utility-first CSS framework that provides pre-defined classes for building custom UI designs. It aims to make the development process faster and more efficient by reducing the need for custom CSS styles.'
    },
    {
      question: 'What are hooks in React?',
      answer:
        'Hooks are functions that allow developers to use state and other React features in functional components. They were introduced in React 16.8 and have become an essential part of React development.'
    },
    {
      question: 'What is useState() hook?',
      answer:
        'useState() is a built-in React hook that allows developers to add state to functional components. It takes an initial value as a parameter and returns an array with the current state value and a function to update that value.'
    },
    {
      question: 'What is the purpose of useEffect() hook?',
      answer:
        'useEffect() is a built-in React hook that allows developers to perform side effects, such as updating the DOM or fetching data from an API, in functional components. It runs after every render and takes a function as a parameter.'
    }
  ];
```

## In Return:
```jsx
  <div className="lg:w-full md:w-1/2 w-full">
    {questions.map((q, index) => (
      <div key={index} className="my-2 bg-[#F6FAFF] rounded-lg">
        <div className='px-3 pt-1' >
          <button className={`w-full text-left font-medium focus:outline-none flex items-center justify-between text-[#777B84] pb-1 ${activeIndex === index && 'text-[#0082C4]  border-b border-[#E4F0FF]'}`}
            onClick={() => handleClick(index)}
          >
            <span>{q.question}</span>
            {activeIndex === index ? (
              <HiMinus size={20} className='font-semibold text-[#0082C4]' />
            ) : (
              <HiPlus size={20} className='font-semibold text-[#0082C4]'  />
            )}
          </button>
        </div>
        <div className={`accordion-answer px-3 pb-1 text-[#777B84] ${
            activeIndex === index && 'accordion-answer-open'
          }`}
        >
          {q.answer}
        </div>
      </div>
    ))}
  </div>
```

## CSS
```jsx
.accordion-answer {
  max-height: 0;
  overflow: hidden;
  transition: max-height 0.1s ease-out;
}


.accordion-answer-open {
  max-height: 500px;
  transition: max-height 0.3s ease-in;
}
```
