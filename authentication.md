---
description: Materially supports 3 popular Authentication methods.
---

# Authentication

Materially supports 3 authentication methods:  **Firebase Authentication, JSON Web Token, Auth0**.

**FYI** - We provide Firebase Authentication by default.

## How does it work?

Only authenticated users can access dashboard pages. If a user is not authenticated, the user redirected to the login page.

We implemented to make this work the “Guard” concept from Angular. It is simply a component that wraps a route and checks for user authentication status before allowing the navigation.&#x20;

We used two guards **GuestGuard** and **AuthGuard**, To find more information about guards, please visit the **Routes.js** page.

&#x20;In the `src/layout/App.js`,  we have specified  auth provider **FirebaseProvider** like,

```
import { FirebaseProvider } from "../contexts/FirebaseContext";
```

App component wrap with the provider, like

```
<ThemeProvider theme={theme(customization)}>
  <FirebaseProvider>
    <Routes />
    <Snackbar />
  </FirebaseProvider>
</ThemeProvider>
```

&#x20;Using **FirebaseProvider**, we can use the context directly by importing `useContext` from React and specifying the context **FirebaseContext** that we want to use or we can use the custom hook **`useAuth`** from `src/hooks/useAuth.js`

## Auth Configuration:

{% hint style="info" %}
You can edit this file at **`[ ../.env]`**
{% endhint %}

```
REACT_APP_VERSION = Version of app
GENERATE_SOURCEMAP = false

## Firebase - Google Auth 

REACT_APP_FIREBASE_API_KEY= Firebase Api key
REACT_APP_FIREBASE_AUTH_DOMAIN=  Firebase Auth domain
REACT_APP_FIREBASE_PROJECT_ID= Firebase Project Id
REACT_APP_FIREBASE_STORAGE_BUCKET= Firebase Storage Bucket
REACT_APP_FIREBASE_MESSAGING_SENDER_ID= Firebase Messaging Sender Id
REACT_APP_FIREBASE_APP_ID= Firebase App Id
REACT_APP_FIREBASE_MEASUREMENT_ID= Firebase Measurement Id

## Auth0

REACT_APP_AUTH0_CLIENT_ID= Auth0 Client Id
REACT_APP_AUTH0_DOMAIN= Auth0 Domain

## JWT

REACT_APP_JWT_SECRET_KEY= Secret key
REACT_APP_JWT_TIMEOUT= Timeout
```

### &#x20;<a href="#switching-between-auth-methods" id="switching-between-auth-methods"></a>

## Switching between Authentication methods

### **Firebase to JWT**

**Set JWT Config** - Open file '**.env**' at directory '../.env' and set **jwt** configuration.

```
## JWT

REACT_APP_JWT_SECRET_KEY= Secret key
REACT_APP_JWT_TIMEOUT= Timeout
```

**Change Login Form** - Open file '**index.js**' at directory '../src/views/Login/index.js', and use the **JWTLogin** component.

```
// Replace at line 8:
import JWTLogin from './JWTLogin';

// Replace at line 21: 
<JWTLogin />
```

**AuthProvider for Layout** - Open file '**App.js**' at directory '../src/layout/App.js' and use **JWTProvider**

```
// Replace at line 6;
import { JWTProvider } from "./contexts/JWTContext";

// Replace from line 22:
<JWTProvider>
    <Routes />
    <Snackbar />
</JWTProvider>
```

&#x20;**Change auth Hooks** - Open file '**useAuth.js**' at directory '../src/hooks/useAuth.js' and use **JWTContext**

```
// Replace from line 2:
import JWTContext from '../contexts/JWTContext';
const useAuth = () => useContext(JWTContext);
```

###

### **Firebase to Auth0**

**Set Auth Config** - Open file '**.env**' at directory '../.env' and set **auth0** configuration.

```
## Auth0

REACT_APP_AUTH0_CLIENT_ID= Auth0 Client Id
REACT_APP_AUTH0_DOMAIN= Auth0 Domain
```

**Change Login Form** - Open file '**index.js**' at directory '../src/views/Login//index.js', and use **Auth0Login** component.

```
// Replace at line 8:
import Auth0Login from './Auth0Login';

// Replace at line 21: 
<Auth0Login />
```

**AuthProvider for Layout** - Open file '**App.js**' at directory '../src/layout/App.js' and use **Auth0Provider**

```
// Replace at line 6;
import { Auth0Provider } from "./contexts/Auth0Context";

// Replace from line 22:
<Auth0Provider>
    {renderRoutes(routes)}
</Auth0Provider>
```

&#x20;**Change auth Hooks** - Open file '**useAuth.js**' at directory '../src/hooks/useAuth.js' and use **Auth0Context**

```
// Replace from line 2:
import Auth0Context from '../contexts/Auth0Context';
const useAuth = () => useContext(Auth0Context);
```
