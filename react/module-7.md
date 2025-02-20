# First Project in React

## 1. **Introduction**
Creating a React project for the first time can be exciting. React is a JavaScript library used to build user interfaces efficiently. This guide walks you through setting up and running your first React project using Vite, a modern build tool for fast development.

---

## 2. **Prerequisites**
Before starting, ensure you have the following installed:
- **Node.js** (Recommended: LTS version) - [Download here](https://nodejs.org/)
- **npm** (Comes with Node.js) or **Yarn**

Check if Node.js and npm are installed by running:
```sh
node -v
npm -v
```

---

## 3. **Setting Up Your First React Project**

### **Step 1: Create a New React Project Using Vite**
Vite is a fast alternative to Create React App (CRA). To create a project, run:
```sh
npm create vite@latest my-first-react-app --template react
```
OR (Using Yarn):
```sh
yarn create vite@latest my-first-react-app --template react
```

### **Step 2: Navigate to the Project Directory**
```sh
cd my-first-react-app
```

### **Step 3: Install Dependencies**
```sh
npm install
```
OR
```sh
yarn install
```

### **Step 4: Start the Development Server**
```sh
npm run dev
```
OR
```sh
yarn dev
```
This will start the development server at `http://localhost:5173/`.

---

## 4. **Understanding the Project Structure**
After setting up, your project directory will look like this:
```
my-first-react-app/
├── node_modules/
├── public/
│   ├── index.html
├── src/
│   ├── App.jsx
│   ├── main.jsx
│   ├── components/
├── .gitignore
├── package.json
├── vite.config.js
└── README.md
```
- `src/App.jsx` - Main React component.
- `src/main.jsx` - Renders the React app.
- `public/index.html` - Entry point of the app.
- `vite.config.js` - Vite configuration file.

---

## 5. **Modifying the Default App Component**
Edit `src/App.jsx` to display a custom message:
```jsx
function App() {
  return (
    <div>
      <h1>My First React Project!</h1>
      <p>Welcome to React development.</p>
    </div>
  );
}
export default App;
```
Save the file, and see the updated content in your browser.

---

## 6. **Building for Production**
To generate an optimized production build, run:
```sh
npm run build
```
This will create a `dist/` folder with the production-ready files.

To preview the build, run:
```sh
npm run preview
```

---

## 7. **Conclusion**
You have successfully set up and built your first React project using Vite! This foundational setup allows you to start exploring component-based development, hooks, and state management.

