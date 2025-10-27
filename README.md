# Getting Started with the Vue Diagram Component in Vue 3

This sample project demonstrates how to create an organizational chart using the Syncfusion Vue Diagram component in a Vue 3 application. The project showcases hierarchical data binding and automatic layout features to create a professional-looking organizational structure.

## Project Overview

The sample implements the following key features:
1. Organizational Chart Layout
2. Hierarchical Data Binding
3. Custom Node and Connector Styling
4. Automatic Layout Arrangement

## Project Structure

```
vue3-diagram-getting-started/
├── public/
│   └── index.html          # HTML entry point
├── src/
│   ├── App.vue            # Main application component
│   ├── main.js           # Vue application entry point
│   ├── assets/           # Static assets
│   └── components/       # Vue components
└── package.json         # Project dependencies and scripts
```

## Technical Implementation

### Data Structure

The organizational chart is built using a hierarchical data structure where each node represents an employee with the following properties:
- Name: Employee's name
- Role: Employee's role/position
- ReportingPerson: Manager's name (for establishing hierarchy)

### Component Features

The Diagram component is configured with the following features:

1. **Node Configuration**:
   - Fixed dimensions: 150px width, 60px height
   - Custom styling with blue background (#6BA5D7)
   - Dual annotations for displaying name and role

2. **Connector Configuration**:
   - Orthogonal type connectors
   - Custom styling with blue stroke (#6BA5D7)
   - Custom arrow decorators

3. **Layout Settings**:
   - Type: OrganizationalChart
   - Automatic node arrangement
   - Hierarchical structure

### Implementation Details

1. **Data Binding**:
```javascript
dataSourceSettings: {
  id: "Name",
  parentId: "ReportingPerson",
  dataManager: new DataManager(localdata)
}
```

2. **Node Customization**:
```javascript
getNodeDefaults: (node) => {
  node.height = 60;
  node.width = 150;
  return node;
}
```

3. **Connector Styling**:
```javascript
getConnectorDefaults: (obj) => {
  obj.type = "Orthogonal";
  obj.style = {
    strokeColor: "#6BA5D7",
    fill: "#6BA5D7",
    strokeWidth: 2
  };
  return obj;
}
```

## Prerequisites

[System requirements for Syncfusion® Vue UI components](https://ej2.syncfusion.com/vue/documentation/system-requirements/)

## Set up the Vite project

A recommended approach for beginning with Vue is to scaffold a project using [Vite](https://vitejs.dev/). To create a new Vite project, use one of the commands that are specific to either NPM or Yarn.

```bash
npm create vite@latest
```

or

```bash
yarn create vite
```

Using one of the above commands will lead you to set up additional configurations for the project as below:

1.Define the project name: We can specify the name of the project directly. Let's specify the name of the project as `my-project` for this article.

```bash
? Project name: » my-project
```

2.Select `Vue` as the framework. It will create a Vue 3 project.

```bash
? Select a framework: » - Use arrow-keys. Return to submit.
Vanilla
> Vue
  React
  Preact
  Lit
  Svelte
  Others
```

3.Choose `JavaScript` as the framework variant to build this Vite project using JavaScript and Vue.

```bash
? Select a variant: » - Use arrow-keys. Return to submit.
> JavaScript
  TypeScript
  Customize with create-vue ↗
  Nuxt ↗
```

4.Upon completing the aforementioned steps to create the `my-project`, run the following command to install its dependencies:

```bash
cd my-project
npm install
```

or

```bash
cd my-project
yarn install
```

Now that `my-project` is ready to run with default settings, let's add Syncfusion® components to the project.

## Add Syncfusion® Vue packages

Syncfusion® Vue component packages are available at [npmjs.com](https://www.npmjs.com/search?q=ej2-vue). To use Syncfusion® Vue components in the project, install the corresponding npm package.

This article uses the [Vue Diagram component](https://www.syncfusion.com/vue-components/vue-diagram) as an example. To use the Vue Diagram component in the project, the `@syncfusion/ej2-vue-diagrams` package needs to be installed using the following command:

```bash
npm install @syncfusion/ej2-vue-diagrams --save
```

or

```bash
yarn add @syncfusion/ej2-vue-diagrams
```

## Import Syncfusion® CSS styles

You can import themes for the Syncfusion® Vue component in various ways, such as using CSS or SASS styles from npm packages, CDN, [CRG](https://ej2.syncfusion.com/javascript/documentation/common/custom-resource-generator/) and [Theme Studio](https://ej2.syncfusion.com/vue/documentation/appearance/theme-studio/). Refer to [themes topic](https://ej2.syncfusion.com/vue/documentation/appearance/theme/) to know more about built-in themes and different ways to refer to themes in a Vue project.

In this article, `Material` theme is applied using CSS styles, which are available in installed packages. The necessary `Material` CSS styles for the Diagram component and its dependents were imported into the `<style>` section of **src/App.vue** file.

{% tabs %}
{% highlight html tabtitle="~/src/App.vue" %}

<style>
    @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
    @import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";
    @import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
    @import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
    @import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
    @import "../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>

{% endhighlight %}
{% endtabs %}

> The order of importing CSS styles should be in line with its dependency graph.

## Run the project

To run the project, use the following command:

```bash
npm run dev
```

or

```bash
yarn run dev
```

## Result

The final output displays an organizational chart with:
- Hierarchical employee structure
- Professional blue color scheme
- Clear reporting relationships
- Responsive layout
- Smooth connector lines
- Role-based node content

## Additional Features

1. **Snap Settings**: The diagram has snap constraints disabled for free-form movement
2. **Responsive Design**: The diagram adjusts to container size (1300px × 800px)
3. **Custom Node Content**: Each node displays both employee name and role
4. **Visual Hierarchy**: Clear parent-child relationships with orthogonal connectors

> **Sample**: [vue-3-diagram-getting-started](https://github.com/SyncfusionExamples/EJ2-Vue3-gettingstarted).

For migrating from Vue 2 to Vue 3, refer to the [`migration`](https://ej2.syncfusion.com/vue/documentation/getting-started/vue3-tutorial/#migration-from-vue-2-to-vue-3) documentation.
