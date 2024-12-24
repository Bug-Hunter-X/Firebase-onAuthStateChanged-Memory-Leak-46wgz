# Firebase onAuthStateChanged Memory Leak
This repository demonstrates a common error when using Firebase's `onAuthStateChanged` method: forgetting to unsubscribe from the listener.  This can lead to memory leaks, particularly in applications that maintain persistent connections.

## The Problem
The `onAuthStateChanged` function returns an unsubscribe function. If you don't call this function when it's no longer needed (e.g., when the component unmounts in React or when your app closes), the listener remains active, consuming memory.

## The Solution
Always store the unsubscribe function returned by `onAuthStateChanged` and call it when it's appropriate to detach the listener. This prevents memory leaks and improves the efficiency of your Firebase application.

## How to Reproduce
1. Clone this repository.
2. Run `npm install` to install the necessary dependencies.
3. Observe the memory usage in your browser's developer tools. You'll likely see a memory increase over time if you don't uncomment the `unsubscribe()` call.
4. Uncomment `unsubscribe();` and rerun to observe corrected memory behavior.