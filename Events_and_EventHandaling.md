## 2️⃣ Events & Event Handling
### 🧠 What is an Event?
• Website-er sathe user ja kichu kore (e.g., Click kora, type kora, scroll kora) shetai ekta Event. 

• Event Listener: Eita ekta function ja shob somoy opekkha kore kokhon nirdishto event-ti ghotbe ebong ghotar sathe sathe code execute kore.

---

### ⚙️ Event Binding
``` js
    const btn = document.querySelector("button");

    // Modern Way: addEventListener (Best Practice)
    btn.addEventListener("click", () => {
        console.log("Button Clicked!");
    });

    // removeEventListener: Event shoriye felar jonno (Function alada hote hoy)
    function greet() { console.log("Hi"); }
    btn.addEventListener("click", greet);
    btn.removeEventListener("click", greet);
```

---

### 🔍 Common Events
| Event       | When it happens? |
|------------|------------------|
| `click`     | Jokhkon kono element-e click kora hoy |
| `input`     | Jokhkon input field-e kichu type kora hoy (protiti okkhore kaj kore) |
| `change`    | Input shesh kore field-er baire click korle |
| `submit`    | Jokhkon kono `<form>` submit kora hoy |
| `mouseover` | Mouse jokhkon element-er upore ashe |
| `keyup`     | Keyboard theke button chere dile |


### 📦 Event Object (e)
Event jokhkon ghote, tokhon browser amader ekta Object dey jate event-er shob tottho thake.
```js
    const btn = document.querySelector("button");

    btn.addEventListener("click", (e) => {
        console.log(e.target);  // Kon element-e click hoyeche (Target)
        console.log(e.type);    // Event-er nam ki (e.g., click)
    });

    // preventDefault(): Browser-er default kaj thamano
    // e.g., Form submit hoye page reload howa thamano
    const form = document.querySelector("form");
    form.addEventListener("submit", (e) => {
        e.preventDefault(); 
        console.log("Form submitted without reload!");
    });
```

---

### 🌊 Bubbling, Capturing & Delegation
#### 1. Bubbling vs Capturing
 • Bubbling (Default): Event niche theke uporer dike jay (Child -> Parent).

 • Capturing: Event upor theke nicher dike ashe (Parent -> Child).

#### 2. Event Delegation (Smart Way) 🧠
Protiti Child-e alada kore event na bosiye tader Parent-e ekti event bosano-ke delegation bole. 
Eita performance-er jonno bhalo.
```js
   const list = document.querySelector("ul");

    list.addEventListener("click", (e) => {
        // e.target check kore bujha jay thik kon li-te click hoyeche
        if(e.target.nodeName === "LI") {
            e.target.style.color = "red"; 
        }
    });


    ⚠️ Confusion Corner
    event.target vs event.currentTarget
    target: Jekhane ashole click kora hoyeche (Deepest element).
    
    currentTarget: Jar gaye event listener lagano hoyeche (Parent element).
    
    Bubbling Phase vs Capturing Phase
    Beshi vag somoy amra Bubbling use kori.
    Jodi addEventListener-er 3rd parameter true dei, tobei sheta Capturing phase-e kaj korbe.
```

---

### ⚡ Important Notes
 • Don't Overbind: Ekti page-e 100-ta button-e 100-ta listener na bosiye Delegation use kora performance-er jonno bhalo.

 • Arrow Functions in Events: Event-er bhetore this use korte chaile Regular Function use kora safe, karun Arrow function-e this thikmoto kaj kore na (Global window-ke dhore fele).

