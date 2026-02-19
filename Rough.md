
Index.js
```JavaScript
import React from "react";

import ReactDOM from "react-dom";

import "./index.css";

import App from "./App";

import { SnackbarProvider } from "notistack";

  

// TODO: CRIO_TASK_MODULE_REGISTER - Add Target container ID (refer public/index.html)

ReactDOM.render(

  <React.StrictMode>

        <SnackbarProvider

          maxSnack={1}

          anchorOrigin={{

            vertical: "bottom",

            horizontal: "center",

          }}

          preventDuplicate

        >

          <App />

        </SnackbarProvider>

  </React.StrictMode>,

   document.getElementById('root')

);
```

App.js

```JavaScript
import Register from "./components/Register";

import ipConfig from "./ipConfig.json";

  

export const config = {

  endpoint: `http://${ipConfig.workspaceIp}:8082/api/v1`,

};

  

function App() {

  return (

    <div className="App">

          <Register />

    </div>

  );

}

  

export default App;
```