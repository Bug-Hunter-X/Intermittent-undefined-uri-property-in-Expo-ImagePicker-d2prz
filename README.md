# Expo ImagePicker - Intermittent undefined uri

This repository demonstrates a bug in Expo's ImagePicker library where the `uri` property of the selected image is sometimes `undefined` after successful image selection.  The issue is intermittent and not consistently reproducible.

## Bug Description
The problem arises when trying to access the `uri` property immediately after using `ImagePicker.launchImageLibraryAsync`.  Sometimes the property is undefined, even though image selection was completed successfully.  This appears to be due to the asynchronous nature of the library and timing issues. 

## How to Reproduce
1. Clone this repository.
2. Run `npm install`
3. Run the app using Expo Go or EAS.
4. Attempt to select an image multiple times.  You will intermittently observe the error.

## Solution
The solution involves properly handling the asynchronous nature of the `launchImageLibraryAsync` method by ensuring the `uri` property is accessed only after the promise resolves and the image data is fully available.  See `bugSolution.js` for a corrected implementation.

## Note
This bug highlights the importance of handling asynchronous operations correctly when dealing with libraries such as Expo ImagePicker.