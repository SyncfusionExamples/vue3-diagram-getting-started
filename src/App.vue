<template>
  <ejs-diagram
    id="diagram"
    :width="width"
    :height="height"
    :getNodeDefaults="getNodeDefaults"
    :getConnectorDefaults="getConnectorDefaults"
    :layout="layout"
    :dataSourceSettings="dataSourceSettings"
    :snapSettings="snapSettings"
  >
  </ejs-diagram>
</template>

<script>
import {
  DiagramComponent,
  DataBinding,
  HierarchicalTree,
  SnapConstraints,
} from "@syncfusion/ej2-vue-diagrams";

import { DataManager } from "@syncfusion/ej2-data";

export let localdata = [
  {
    Name: "Elizabeth",
    Role: "Editor",
  },
  {
    Name: "Christina",
    ReportingPerson: "Elizabeth",
    Role: "Managing Editor",
  },
  {
    Name: "Yoshi",
    ReportingPerson: "Christina",
    Role: "Assistant Editor",
  },
  {
    Name: "Philip",
    ReportingPerson: "Christina",
    Role: "Copy Editor",
  },
  {
    Name: "Yang",
    ReportingPerson: "Elizabeth",
    Role: "Bussiness Editor",
  },
  {
    Name: "Roland",
    ReportingPerson: "Yang",
    Role: "Assistant Editor",
  },
  {
    Name: "Yvonne",
    ReportingPerson: "Yang",
    Role: "Editorial Assistant",
  },
];

export default {
  name: "App",
  components: {
    "ejs-diagram": DiagramComponent,
  },
  data() {
    return {
      width: "1300px",
      height: "800px",
      snapSettings: { constraints: SnapConstraints.None },
      getNodeDefaults: (node) => {
        node.height = 60;
        node.width = 150;
        return node;
      },
      getConnectorDefaults: (obj) => {
        obj.type = "Orthogonal";
        obj.style = {
          strokeColor: "#6BA5D7",
          fill: "#6BA5D7",
          strokeWidth: 2,
        };
        obj.targetDecorator = {
          style: {
            fill: "#6BA5D7",
            strokeColor: "#6BA5D7",
          },
        };
        return obj;
      },
      layout: {
        type: "OrganizationalChart",
      },
      dataSourceSettings: {
        id: "Name",
        parentId: "ReportingPerson",
        dataManager: new DataManager(localdata),
        doBinding: (nodeModel, localdata) => {
          nodeModel.annotations = [
            {
              content: localdata.Name,
              offset: { x: 0.5, y: 0.2 },
              style: { color: "white" },
            },
            {
              content: localdata.Role,
              offset: { x: 0.5, y: 0.7 },
              style: { color: "white" },
            },
          ];
          nodeModel.style = { fill: "#6BA5D7", strokeWidth: 0 };
        },
      },
    }
  },
  provide: { diagram: [DataBinding, HierarchicalTree] },
};
</script>

<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-dropdowns/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
@import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";
</style>
