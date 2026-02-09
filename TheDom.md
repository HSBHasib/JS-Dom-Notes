## 1️⃣ The DOM (Document Object Model)

### 🧠 What is DOM?
• DOM is the "Brain" of your webpage. 

• It represents the HTML document as a Tree structure. 

• JS uses the DOM to change content, style, and structure dynamically.

---

### 🌳 DOM Tree Structure
``` js
    Every part of the HTML is a Node: 
    • Element Node: <div>, <h1>, <p> etc. 
    • Text Node: The actual text inside an element. 
    • Attribute Node: class, id, src etc. 
    • Comment Node: HTML comments.
```


---

### 🔍 Selecting Elements
```js
    // 1. By ID (Unique)
    const title = document.getElementById("main-title");

    // 2. By Class Name (Returns HTMLCollection)
    const items = document.getElementsByClassName("list-item");

    // 3. Query Selector (Modern & Powerful)
    const header = document.querySelector("h1");      // First <h1> match
    const nav = document.querySelector(".navbar");    // First class match

    // 4. Query Selector All (Returns static NodeList)
    const allParas = document.querySelectorAll("p");  // Select All p tag    
```

### 🗺️ DOM Navigation (Moving around)
Ekta element theke tar parent ba sibling-e jaoar jonno eita dorkar.
```js
    {
    //HTML Code
    <ul id="parent-list">
        <li>Item 1</li>
        <li class="list-item">Item 2 (Target)</li>
        <li>Item 3</li>
    </ul>
    {


    // JS Code
    const item = document.querySelector(".list-item"); // Targetting Item 2

    // 1. Parent Navigation
    console.log(item.parentElement);      
    // Output: <ul id="parent-list">...</ul>

    // 2. Child Navigation (Parent theke niche)
    const list = document.querySelector("#parent-list");
    console.log(list.children);           // Output: [li, li.list-item, li] (HTMLCollection)
    console.log(list.firstElementChild);  // Output: <li>Item 1</li>

    // 3. Sibling Navigation (Pasher element)
    console.log(item.nextElementSibling);     // Output: <li>Item 3</li>
    console.log(item.previousElementSibling); // Output: <li>Item 1</li>
```

---

### 📝 Accessing & Changing Content
```js
   let box = document.querySelector(".box");

    box.innerText;   // Visible text only (respects CSS)
    box.textContent; // All text (including hidden text)
    box.innerHTML;   // Text + HTML tags inside

    // ⚠️ innerText shudhu manush ja dekhe tai dey,
        kintu innerHTML pura HTML structure-ta change ba read korte pare.
```

---

### 🛠️ Attribute Manipulation
```js
    const img = document.querySelector("img");

    img.getAttribute("src");             // Get value
    img.setAttribute("src", "new.jpg");  // Change value
    img.removeAttribute("alt");          // Remove attribute
```

---

### 🎨 Style & Classes
```js
    const el = document.querySelector(".text");

    // via .style (Inline CSS - use CamelCase)
    el.style.backgroundColor = "yellow"; 

    // via classList (Recommended)
    el.classList.add("active");
    el.classList.remove("hidden");
    el.classList.toggle("dark-mode"); // Adds if missing, removes if exists
```

---

### 🏗️ Dynamic DOM Manipulation
#### 1. Creating Elements
```js
    const newDiv = document.createElement("div"); // Element toiri holo
    newDiv.innerText = "I am a new div!";         // Content dewa holo
    newDiv.classList.add("box");                  // Style/Class add holo
```

#### 2.Adding to Page (Insertion Methods)
Notun element-ta kothay thakbe sheta niche dewa holo:
```js
    const container = document.querySelector(".main");

    // 1. appendChild (Old School & Specific)
    container.appendChild(newDiv); 
    // • Shudhu 'Node' (element) add kora jay.
    // • Shob somoy parent-er shobar sheshe add hoy.

    // 2. append (Modern & Flexible)
    container.append(newDiv, "Just some text"); 
    // • Notun element + Text eksathe add kora jay.
    // • Eitao parent-er shobar sheshe add hoy.

    // 3. prepend
    container.prepend(newDiv); 
    // • Element-ke parent-er ekdom shuru-te (First child) niye jay.

    // 4. insertAdjacentElement (More Precise Control)
    const btn = document.querySelector("button");
    btn.insertAdjacentElement('beforebegin', newDiv);
 
    // Options: 'beforebegin' (agey),
    //          'afterbegin' (bhetore shurute), 
    //          'beforeend' (bhetore sheshe),
    //          'afterend' (pore).
```

---

#### 📌 appendChild() vs append()

| Feature            | appendChild()                | append()                         |
|--------------------|------------------------------|----------------------------------|
| Supports Text?     | ❌ No (Only Element Node)     | ✅ Yes (Text & Element)           |
| Multiple Items?    | ❌ No (Only one)              | ✅ Yes (Multiple items)           |
| Return Value?      | ✅ Returns the added node     | ❌ Returns `undefined`            |

---

#### 3. Removing Elements
```js
    const item = document.querySelector(".list-item");

    // Modern way: Shorasori remove
    item.remove(); 

    // Old way: Parent theke remove kora
    const list = document.querySelector("ul");
    list.removeChild(item);
```

---

### ⚡ Important Notes
#### 📌 innerText vs innerHTML
```js
- **innerText** → shudhu user je text-ta screen-e dekhe, shetai dey  
- **innerHTML** → puro HTML structure (tags সহ) read & change korte pare
```

---

#### 📌 HTMLCollection vs NodeList
| Feature           | HTMLCollection                    | NodeList                           |
|-------------------|-----------------------------------|------------------------------------|
| Returned by       | `getElementsBy...`                | `querySelectorAll()`               |
| Nature            | 🔄 Live (Auto updates)            | 🧊 Static (Doesn't update)          |
| Array Methods     | ❌ Not supported                  | ✅ Supports `.forEach()`            |

