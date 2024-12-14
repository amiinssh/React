# Calculator App

This project is a simple, responsive calculator built with React. It demonstrates the use of React's `useReducer` hook to manage state and a clean design for user interactions.

## Features
- **Basic Arithmetic**: Perform addition, subtraction, multiplication, and division.
- **Clear and Delete**: Clear all inputs or delete the last entered digit.
- **Decimal Support**: Includes support for decimal numbers.
- **Formatted Output**: Numbers are formatted using `Intl.NumberFormat` for better readability.
- **Responsive Design**: Works well on different screen sizes with a visually appealing layout.

## Project Structure

```plaintext
.
├── src
│   ├── App.js                # Main component containing the calculator logic and UI.
│   ├── DigitButton.js        # Component for digit buttons (0-9 and decimal point).
│   ├── OperationButton.js    # Component for operation buttons (+, -, *, /).
│   ├── styles.css            # Styles for the calculator layout and components.
├── public
│   ├── index.html            # HTML entry point.
├── package.json              # Project dependencies and scripts.
```

## Code Overview

### `App.js`
- Contains the main logic using the `useReducer` hook.
- Defines the `ACTIONS` constants for dispatch actions.
- Implements the `reducer` function for state transitions.
- Renders the calculator layout and connects components.

### `DigitButton.js` and `OperationButton.js`
- **`DigitButton`**: Renders buttons for digits and passes dispatch actions for digit input.
- **`OperationButton`**: Renders buttons for operations and passes dispatch actions for operation selection.

### `styles.css`
- Styles the calculator with a grid-based layout.
- Includes hover and focus effects for buttons.
- Adds a gradient background for aesthetic appeal.

## Example Code Snippet

```javascript
function reducer(state, { type, payload }) {
  switch (type) {
    case ACTIONS.ADD_DIGIT:
      if (state.overwrite) {
        return { ...state, currentOperand: payload.digit, overwrite: false };
      }
      if (payload.digit === "0" && state.currentOperand === "0") return state;
      if (payload.digit === "." && state.currentOperand.includes(".")) return state;
      return {
        ...state,
        currentOperand: `${state.currentOperand || ""}${payload.digit}`,
      };
    case ACTIONS.CHOOSE_OPERATION:
      if (!state.currentOperand && !state.previousOperand) return state;
      return {
        ...state,
        previousOperand: evaluate(state),
        operation: payload.operation,
        currentOperand: null,
      };
    case ACTIONS.EVALUATE:
      if (!state.operation || !state.currentOperand || !state.previousOperand) return state;
      return {
        ...state,
        overwrite: true,
        currentOperand: evaluate(state),
        operation: null,
        previousOperand: null,
      };
    case ACTIONS.CLEAR:
      return {};
    case ACTIONS.DELETE_DIGIT:
      if (!state.currentOperand) return state;
      return {
        ...state,
        currentOperand: state.currentOperand.slice(0, -1),
      };
    default:
      return state;
  }
}
```

## Future Improvements
- Add advanced operations like square root or exponentiation.
- Implement memory functions (M+, M-, MR).
- Enhance styling with animations or themes.

