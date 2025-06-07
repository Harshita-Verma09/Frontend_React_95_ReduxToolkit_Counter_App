# Redux Toolkit Counter Example

This repository contains a basic counter application built with React and Redux Toolkit. It demonstrates the core concepts of Redux Toolkit, including `createSlice` for defining reducers and actions, and how to use `useSelector` and `useDispatch` hooks in React components.

## Table of Contents

- [Introduction](#introduction)
- [Project Structure](#project-structure)
- [Key Concepts Explained](#key-concepts-explained)
  - [`createSlice`](#createslice)
  - `useSelector`
  - `useDispatch`
- [Setup and Installation](#setup-and-installation)
- [Usage](#usage)

## Introduction

This example provides a clear and concise illustration of how to manage state in a React application using Redux Toolkit. It features a simple counter that can be incremented, decremented, and reset.

## Project Structure

The relevant files for this example are:

- `src/features/counterSlice.js`: Defines the Redux slice for the counter state.
- `src/App.js`: The main React component that consumes the Redux state and dispatches actions.

*(Note: In a real application, you would also have an `index.js` or `main.jsx` to set up your Redux store and wrap your `App` component with a `Provider` from `react-redux`.)*

## Key Concepts Explained

### `createSlice`

Redux Toolkit's `createSlice` is a powerful function that simplifies the process of creating Redux reducers and actions. It automatically generates action creators and action types based on the `reducers` object you provide.

In `src/features/counterSlice.js`:

```javascript
// src/features/counterSlice.js
import { createSlice } from '@reduxjs/toolkit';

const counterSlice = createSlice({
  name: 'counter', // The name of the slice, used as a prefix for generated action types
  initialState: {
    value: 0 // The initial state for this slice
  },
  reducers: {
    // Reducer functions that directly modify the state (thanks to Immer.js)
    increment: (state) => {
      state.value += 1;
    },
    decrement: (state) => {
      state.value -= 1;
    },
    reset: (state) => {
      state.value = 0;
    }
  }
});

// Export the generated action creators
export const { increment, decrement, reset } = counterSlice.actions;

// Export the reducer for this slice
export default counterSlice.reducer;
