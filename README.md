# React Native useEffect Hook with Function Dependency Issue

This repository demonstrates a common but subtle bug in React Native when using the `useEffect` hook with a function in the dependency array.  The issue stems from React Native's inability to detect changes in the function's internal state, resulting in the effect not re-running as expected when the function's logic changes.

## Problem

The `useEffect` hook is designed to perform side effects based on changes in its dependencies.  However, when a function is included in the dependency array, the effect might not trigger updates even if the function's logic changes because React Native's reference comparison for functions only checks for identity, not for changes in their internal state.

## Solution

The provided solution utilizes a unique key generated from the function's source code. By using this key as a dependency, React Native triggers the effect whenever the function's logic is altered.