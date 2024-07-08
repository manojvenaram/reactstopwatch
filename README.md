## StopWatch-React

### App.js:
~~~
import {useState,useRef} from "react";
import './App.css';

function App() {
  const [time , setTime] = useState(null);
  const [now,setNow]=useState(null);

  const intervalRef = useRef(null);
  const [diff,setDiff]=useState(0);
  // const [first,setFirst]=useState(0);
  const handleStart=()=>{

    setTime(Date.now());
    setNow(Date.now()-diff);
    intervalRef.current=setInterval(() => {
      setTime(Date.now());
    },10);
    
  };

  const handleStop=()=> {
    setDiff(time-now);
    clearInterval(intervalRef.current);
  }

  const handleReset=()=>{
    setTime(Date.now());
    setNow(Date.now());
    setDiff(0);
    clearInterval(intervalRef.current);
  }

    let timePassed =(time-now);
    let timeMinute=Math.floor(timePassed / (1000*60)%60);
    let timeSecond=Math.floor(timePassed/ (1000)%60);
    let millisecond=Math.floor((timePassed% 1000)/10);

    let minute=String(timeMinute).padStart(2,'0');
    let second=String(timeSecond).padStart(2,'0');
    let milli=String(millisecond).padStart(2,'0');
  return (
    <div className="App">
      <h1>StopWatch</h1>
      <h2>Timer:{minute}:{second}:{milli}</h2>
      <div>
        <button onClick={handleStart}>Start</button>
        <button onClick={handleStop}>Stop</button>
        <button onClick={handleReset}>Reset</button>
      </div>
    </div>
  );
}

export default App;
~~~
### App.css:
~~~
.App {
  text-align: center;
  background-color: aqua;
  height:800px;
}
h1{
  padding-top: 150px;
}
button{
  margin: 10px;
  padding: 10px;
  font-size: larger;
  border-radius: 20%;
}
~~~
### Output:
(https://manojvenaram.github.io/reactstopwatch/)
![image](https://github.com/RanjithD18/stopwatch/assets/93427221/851b32b0-067c-40be-bc0d-776fcce6b4e9)

![image](https://github.com/RanjithD18/stopwatch/assets/93427221/c9335958-175e-4211-b553-1abdf8b361f6)
