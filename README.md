# Form Helper Chrome

![npm](https://img.shields.io/npm/v/form-helper-chrome)
![npm](https://img.shields.io/npm/dw/form-helper-chrome)
![license](https://img.shields.io/npm/l/form-helper-chrome)

`form-helper-chrome` is an npm package that provides a React component for form error handling using Chrome's Built-in AI. This package leverages AI to generate helpful messages for form errors, enhancing user experience.

## Installation

To install the package, use npm:

```
npm install form-helper-chrome
```


## Usage

To use the `FormHelperChrome` component and `createPrompt` function, import them into your React application:

```
import React from 'react';
import { FormHelperChrome, createPrompt } from 'form-helper-chrome';

const App = () => {
  const formGuideHtml = "<p>Your form guide here</p>";
  const error = {
    name: ['fieldName'],
    errors: ['This field is required'],
    value: '',
    touched: true
  };

  // Create a prompt using the createPrompt function
  const prompt = createPrompt(error, formGuideHtml);

  return (
    <FormHelperChrome
      prompt={prompt}
      fontSize="14px"
      isDarkMode={false}
      plain={false}
    />
  );
};

export default App;
```

![demo](https://github.com/dusskapark/form-helper-chrome-playground/raw/master/demo.gif)


## Custom Prompt

If you prefer to create a custom prompt, you can construct it manually as shown below:

```
const customPrompt = `
  # Custom Form Guide:
  \`\`\`
  ${formGuideHtml}
  \`\`\`

  # Custom Error Description:
  Field: \`${error.name.join(".")}\`
  Value: \`${error.value}\`
  Error: \`${error.errors.join(", ")}\`
  
  Please provide a response in the following format:
  ${outputFormat}
`;
```

You can then pass this `customPrompt` to the `FormHelperChrome` component:


<FormHelperChrome
  prompt={customPrompt}
  fontSize="14px"
  isDarkMode={false}
  plain={false}
/>


## Props

### FormHelperChrome

| Prop Name     | Type     | Default Value       | Required | Description                                                                 |
|---------------|----------|---------------------|----------|-----------------------------------------------------------------------------|
| `prompt`      | `string` | `""`                | Yes      | The prompt string to be sent to the AI for generating a response.           |
| `fontSize`    | `string` | `"16px"`            | No       | Font size for the rendered markdown content.                                |
| `isDarkMode`  | `boolean` | `false`             | No       | Enables dark mode styling if set to `true`.                                 |
| `plain`       | `boolean` | `false`             | No       | If `true`, renders only the markdown content without the card component.    |

### createPrompt

| Parameter       | Type       | Description                                                                 |
|-----------------|------------|-----------------------------------------------------------------------------|
| `error`         | `object`   | An object containing error details for the form field. It includes:         |
|                 |            | - `name`: An array of strings representing the field name(s).               |
|                 |            | - `errors`: An array of error messages related to the field.                |
|                 |            | - `value`: The current value of the field.                                  |
|                 |            | - `touched`: A boolean indicating whether the field has been interacted with.|
| `formGuideHtml` | `string`   | HTML content for the form guide.                                            |
| `outputFormat`  | `string`   | Format for the AI-generated response. Defaults to `DEFAULT_OUTPUT_FORMAT`.  |

## Prerequisites

This package utilizes Chrome's Built-in AI APIs, which require specific browser settings and access permissions. Please follow the steps below to ensure proper setup:

1. **Join the Early Preview Program**: To experiment with Chrome's Built-in AI APIs, you must join the [early preview program](https://forms.gle/ksWMYFtsUSZiC63m9). Upon joining, you will receive access to the setup guide necessary for configuring your browser.

2. **Set Up Chrome Canary or Dev Version**: The AI features are available in the Chrome Canary or Dev versions. Ensure you have the appropriate version installed.

3. **Enable Required Flags**: Follow the instructions provided in the setup guide to enable the necessary flags in your Chrome browser to access the AI APIs.


> For an overview of Chrome's Built-in AI APIs, refer to the [official introduction](https://developer.chrome.com/docs/ai/built-in). 

## License

This project is licensed under the MIT License.