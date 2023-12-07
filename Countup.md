# Countup
This is a countup system that will count any number from 0. It has a visibility sensor that will make sure that user views specific section. This is how we can make it with 2 simple packages.

## Technologies
- ReactJS/NextJS
- TailwindCSS

## Packages
```jsx
npm i react-visibility-sensor
```

```jsx
npm i react-countup
```

## Import 
```jsx
import CountUp from "react-countup";
import VisibilitySensor from "react-visibility-sensor";
```
## Return 
```jsx
  return(
    <p className='font-bold text-4xl flex items-center'>
      <VisibilitySensor
        partialVisibility
        offset={{ bottom: 200 }}
      >
        {({ isVisible }) => (
          <div>
            {isVisible ? <CountUp end={5} duration={1} /> : 30}
          </div>
        )}
      </VisibilitySensor>+
    </p>
)
```
