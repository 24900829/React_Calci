# Ex04 Simple Calculator - React Project
## NAME : KAVIBHARATHI K
## REG NO : 212224220045

## AIM
To  develop a Simple Calculator using React.js with clean and responsive design, ensuring a smooth user experience across different screen sizes.

## ALGORITHM
### STEP 1
Create a React App.

### STEP 2
Open a terminal and run:
  <ul><li>npx create-react-app simple-calculator</li>
  <li>cd simple-calculator</li>
  <li>npm start</li></ul>

### STEP 3
Inside the src/ folder, create a new file Calculator.js and define the basic structure.

### STEP 4
Plan the UI: Display screen, number buttons (0-9), operators (+, -, *, /), clear (C), and equal (=).

### STEP 5
Create a new file Calculator.css in src/ and add the styling.

### STEP 6
Open src/App.js and modify it.

### STEP 7
Start the development server.
  npm start

### STEP 8
Open http://localhost:3000/ in the browser.

### STEP 9
Test the calculator by entering numbers and operations.

### STEP 10
Fix styling issues and refine content placement.

### STEP 11
Deploy the website.

### STEP 12
Upload to GitHub Pages for free hosting.

## PROGRAM

```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>Simple Calculator - React</title>
    <script crossorigin src="https://unpkg.com/react@18/umd/react.development.js"></script>
    <script crossorigin src="https://unpkg.com/react-dom@18/umd/react-dom.development.js"></script>
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
    <style>
      body { font-family: Arial, sans-serif; display:flex;justify-content:center;align-items:center;height:100vh;background:#f3f3f3; }
      .calc { background:#fff; padding:20px; border-radius:12px; box-shadow:0 4px 10px rgba(0,0,0,.1); }
      .display { background:#eee; padding:15px; text-align:right; font-size:24px; margin-bottom:15px; border-radius:8px; }
      .buttons { display:grid; grid-template-columns:repeat(4,60px); gap:10px; }
      button { padding:15px; font-size:18px; border:none; border-radius:8px; cursor:pointer; background:#f0f0f0; }
      button.op { background:#d0e0ff; }
      button.equal { grid-column: span 4; background:#4f46e5; color:white; }
    </style>
  </head>
  <body>
    <div id="root"></div>

    <script type="text/babel">
      function Calculator() {
        const [display, setDisplay] = React.useState("0");
        const [first, setFirst] = React.useState(null);
        const [op, setOp] = React.useState(null);
        const [wait, setWait] = React.useState(false);

        const input = (d) => {
          setDisplay(prev => wait ? (setWait(false), String(d)) : (prev==="0"? String(d): prev+d));
        };
        const dot = () => setDisplay(p => p.includes(".") ? p : p+".");
        const clear = () => { setDisplay("0"); setFirst(null); setOp(null); setWait(false); };
        const calc = (a,b,o) => ({"+":a+b,"-":a-b,"*":a*b,"/":b? a/b : NaN}[o]);
        const choose = (nextOp) => {
          const val = Number(display);
          if(first==null) setFirst(val);
          else if(!wait){ let res = calc(first,val,op); setFirst(res); setDisplay(String(res)); }
          setOp(nextOp); setWait(true);
        };
        const equal = () => { if(op==null) return; let res=calc(first,Number(display),op); setDisplay(String(res)); setFirst(null); setOp(null); };

        return (
          <div className="calc">
            <div className="display">{display}</div>
            <div className="buttons">
              <button onClick={clear}>C</button>
              <button onClick={() => setDisplay(p=>p[0]==='-'?p.slice(1):'-'+p)}>±</button>
              <button onClick={() => setDisplay(p=>String(+p/100))}>%</button>
              <button className="op" onClick={()=>choose("/")}>÷</button>

              {[7,8,9].map(n=><button key={n} onClick={()=>input(n)}>{n}</button>)}
              <button className="op" onClick={()=>choose("*")}>×</button>

              {[4,5,6].map(n=><button key={n} onClick={()=>input(n)}>{n}</button>)}
              <button className="op" onClick={()=>choose("-")}>−</button>

              {[1,2,3].map(n=><button key={n} onClick={()=>input(n)}>{n}</button>)}
              <button className="op" onClick={()=>choose("+")}>+</button>

              <button onClick={()=>setDisplay(p=>p.length>1?p.slice(0,-1):"0")}>⌫</button>
              <button onClick={()=>input(0)}>0</button>
              <button onClick={dot}>.</button>
              <button className="equal" onClick={equal}>=</button>
            </div>
          </div>
        );
      }

      ReactDOM.createRoot(document.getElementById("root")).render(<Calculator />);
    </script>
  </body>
</html>
```

## OUTPUT

<img width="1335" height="799" alt="Screenshot 2025-09-01 113830" src="https://github.com/user-attachments/assets/f7ae2b5a-2bbb-490d-8c8b-6d99dc27ab6c" />



## RESULT
The program for developing a simple calculator in React.js is executed successfully.
