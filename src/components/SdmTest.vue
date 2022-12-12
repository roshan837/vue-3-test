<template>
  <div class="min-w-full min-h-screen" id="cyto"></div>
</template>

<script lang="ts" setup>
import cytoscape from 'cytoscape'
import { onMounted } from 'vue'
import klay from 'cytoscape-klay'
import BubbleSets from 'cytoscape-bubblesets';
import cytoscapeLayers from 'cytoscape-layers'

cytoscape.use(BubbleSets);
cytoscape.use(klay)

const sdmData = {"nodes":[{"id":"2","name":"APS-Cache-Service","type":"cache1_service","title":null,"txnAffected":false,"kpiAffected":false,"metadata":{"jimEnabled":"1"},"rcapathNode":false,"startNode":false,"userAccessible":true,"applicationName":["APS"]},{"id":"3","name":"APS-LB-Service","type":"loadbalancer_service","title":null,"txnAffected":false,"kpiAffected":false,"metadata":{"jimEnabled":"0"},"rcapathNode":false,"startNode":false,"entryPointNode":true,"userAccessible":true,"applicationName":["APS"]},{"id":"4","name":"Control Center","type":"heal_service","title":null,"txnAffected":false,"kpiAffected":false,"metadata":{"jimEnabled":"0"},"rcapathNode":false,"startNode":false,"userAccessible":true,"applicationName":["APS"]},{"id":"5","name":"APS-DB-Service","type":"db_service","title":null,"txnAffected":false,"kpiAffected":false,"metadata":{"jimEnabled":"0"},"rcapathNode":false,"startNode":false,"userAccessible":true,"applicationName":["APS"]},{"id":"8","name":"UPIUSER","type":"user","title":null,"txnAffected":false,"kpiAffected":false,"metadata":{"jimEnabled":"0"},"rcapathNode":false,"startNode":false,"userAccessible":false,"applicationName":["UPI"]},{"id":"9","name":"UPI-DB-Service","type":"db_service","title":null,"txnAffected":false,"kpiAffected":false,"metadata":{"jimEnabled":"0"},"rcapathNode":false,"startNode":false,"userAccessible":false,"applicationName":["UPI"]},{"id":"10","name":"UPI-Weblogic-Service","type":"app_service","title":null,"txnAffected":false,"kpiAffected":false,"metadata":{"jimEnabled":"1"},"rcapathNode":false,"startNode":false,"entryPointNode":true,"userAccessible":false,"applicationName":["UPI"]},{"id":"13","name":"Icustody-DB-Service","type":"db_service","title":null,"txnAffected":false,"kpiAffected":false,"metadata":{"jimEnabled":"0"},"rcapathNode":false,"startNode":false,"userAccessible":true,"applicationName":["Icustody"]},{"id":"7","name":"Icustody-Weblogic-Service","type":"app_service","title":null,"txnAffected":false,"kpiAffected":false,"metadata":{"jimEnabled":"1"},"rcapathNode":false,"startNode":false,"entryPointNode":true,"userAccessible":true,"applicationName":["Icustody"]},{"id":"15","name":"Icustody_User","type":"user","title":null,"txnAffected":false,"kpiAffected":false,"metadata":{"jimEnabled":"0"},"rcapathNode":false,"startNode":false,"userAccessible":true,"applicationName":["Icustody"]},{"id":"18","name":"FCC_User","type":"user","title":null,"txnAffected":false,"kpiAffected":false,"metadata":{"jimEnabled":"0"},"rcapathNode":false,"startNode":false,"userAccessible":true,"applicationName":["FCC"]},{"id":"19","name":"FCC-Web-Service","type":"web_service","title":null,"txnAffected":false,"kpiAffected":false,"metadata":{"jimEnabled":"0"},"rcapathNode":false,"startNode":false,"entryPointNode":true,"userAccessible":true,"applicationName":["FCC"]},{"id":"20","name":"FCC-App-Service","type":"app_service","title":null,"txnAffected":false,"kpiAffected":false,"metadata":{"jimEnabled":"1"},"rcapathNode":false,"startNode":false,"userAccessible":true,"applicationName":["FCC"]},{"id":"21","name":"FCC-DB-Service","type":"db_service","title":null,"txnAffected":false,"kpiAffected":false,"metadata":{"jimEnabled":"0"},"rcapathNode":false,"startNode":false,"userAccessible":true,"applicationName":["FCC"]},{"id":"24","name":"CMSC_User","type":"user","title":null,"txnAffected":false,"kpiAffected":false,"metadata":{"jimEnabled":"0"},"rcapathNode":false,"startNode":false,"userAccessible":true,"applicationName":["CMSC"]},{"id":"25","name":"CMSC_DB_Service","type":"db_service","title":null,"txnAffected":false,"kpiAffected":false,"metadata":{"jimEnabled":"0"},"rcapathNode":false,"startNode":false,"userAccessible":true,"applicationName":["CMSC"]},{"id":"28","name":"LOSUSER","type":"user","title":null,"txnAffected":false,"kpiAffected":false,"metadata":{"jimEnabled":"0"},"rcapathNode":false,"startNode":false,"userAccessible":true,"applicationName":["LOS"]},{"id":"29","name":"LOS-WAS-Service","type":"web_service","title":null,"txnAffected":false,"kpiAffected":false,"metadata":{"jimEnabled":"1","isKubernetes":1},"rcapathNode":false,"startNode":false,"userAccessible":true,"applicationName":["LOS"]},{"id":"30","name":"LOS-DB-Service","type":"db_service","title":null,"txnAffected":false,"kpiAffected":false,"metadata":{"jimEnabled":"0"},"rcapathNode":false,"startNode":false,"userAccessible":true,"applicationName":["LOS"]},{"id":"31","name":"LOS-IHS-Service","type":"web_service","title":null,"txnAffected":false,"kpiAffected":false,"metadata":{"jimEnabled":"0"},"rcapathNode":false,"startNode":false,"entryPointNode":true,"userAccessible":true,"applicationName":["LOS"]},{"id":"36","name":"Murex-DB-Service","type":"app_service","title":null,"txnAffected":false,"kpiAffected":false,"metadata":{"jimEnabled":"0"},"rcapathNode":false,"startNode":false,"userAccessible":true,"applicationName":["Murex"]},{"id":"37","name":"Murex-app-Service","type":"app_service","title":null,"txnAffected":false,"kpiAffected":false,"metadata":{"jimEnabled":"0"},"rcapathNode":false,"startNode":false,"entryPointNode":true,"userAccessible":true,"applicationName":["Murex"]},{"id":"38","name":"Murex_User","type":"user","title":null,"txnAffected":false,"kpiAffected":false,"metadata":{"jimEnabled":"0"},"rcapathNode":false,"startNode":false,"userAccessible":true,"applicationName":["Murex"]},{"id":"41","name":"Axiom-DB-Service","type":"app_service","title":null,"txnAffected":false,"kpiAffected":false,"metadata":{"jimEnabled":"0"},"rcapathNode":false,"startNode":false,"userAccessible":true,"applicationName":["Axiom"]},{"id":"42","name":"Axiom_User","type":"user","title":null,"txnAffected":false,"kpiAffected":false,"metadata":{"jimEnabled":"0"},"rcapathNode":false,"startNode":false,"userAccessible":true,"applicationName":["Axiom"]},{"id":"43","name":"Axiom-app-Service","type":"app_service","title":null,"txnAffected":false,"kpiAffected":false,"metadata":{"jimEnabled":"0"},"rcapathNode":false,"startNode":false,"entryPointNode":true,"applicationName":["Axiom"]},{"id":"46","name":"PG-Weblogic-Service","type":"app_service","title":null,"txnAffected":false,"kpiAffected":false,"metadata":{"jimEnabled":"1"},"rcapathNode":false,"startNode":false,"userAccessible":true,"applicationName":["PG"]},{"id":"47","name":"PG-DB-Service","type":"db_service","title":null,"txnAffected":false,"kpiAffected":false,"metadata":{"jimEnabled":"0"},"rcapathNode":false,"startNode":false,"userAccessible":true,"applicationName":["PG"]},{"id":"48","name":"PGUSER","type":"user","title":null,"txnAffected":false,"kpiAffected":false,"metadata":{"jimEnabled":"0"},"rcapathNode":false,"startNode":false,"userAccessible":true,"applicationName":["PG"]},{"id":"49","name":"PG-Tomcat-Service","type":"web_service","title":null,"txnAffected":false,"kpiAffected":false,"metadata":{"jimEnabled":"0"},"rcapathNode":false,"startNode":false,"userAccessible":true,"applicationName":["PG"]},{"id":"62","name":"MvisaUser","type":"user","title":null,"txnAffected":false,"kpiAffected":false,"metadata":{"jimEnabled":"0"},"rcapathNode":false,"startNode":false,"userAccessible":true,"applicationName":["Mvisa"]},{"id":"63","name":"Mvisa-App-Service","type":"app_service","title":null,"txnAffected":false,"kpiAffected":false,"metadata":{"jimEnabled":"0"},"rcapathNode":false,"startNode":false,"userAccessible":true,"applicationName":["Mvisa"]},{"id":"64","name":"Mvisa-DB-Service","type":"db_service","title":null,"txnAffected":false,"kpiAffected":false,"metadata":{"jimEnabled":"0"},"rcapathNode":false,"startNode":false,"userAccessible":true,"applicationName":["Mvisa"]},{"id":"65","name":"Mvisa-Web-Service","type":"web_service","title":null,"txnAffected":false,"kpiAffected":false,"metadata":{"jimEnabled":"0"},"rcapathNode":false,"startNode":false,"userAccessible":true,"applicationName":["Mvisa"]},{"id":"68","name":"APPSONEUSER","type":"user","title":null,"txnAffected":false,"kpiAffected":false,"metadata":{"jimEnabled":"0"},"rcapathNode":false,"startNode":false,"userAccessible":false,"applicationName":["APPSONE"]},{"id":"69","name":"APPSONE-DB-SERVICE","type":"db_service","title":null,"txnAffected":false,"kpiAffected":false,"metadata":{"jimEnabled":"0"},"rcapathNode":false,"startNode":false,"userAccessible":false,"applicationName":["APPSONE"]},{"id":"70","name":"APPSONE-APP-SERVICE","type":"app_service","title":null,"txnAffected":false,"kpiAffected":false,"metadata":{"jimEnabled":"0"},"rcapathNode":false,"startNode":false,"userAccessible":false,"applicationName":["APPSONE"]}],"edges":[{"source":"4","target":"3","data":{}},{"source":"3","target":"2","data":{}},{"source":"2","target":"5","data":{}},{"source":"8","target":"10","data":{}},{"source":"10","target":"9","data":{}},{"source":"15","target":"7","data":{}},{"source":"7","target":"13","data":{}},{"source":"18","target":"19","data":{}},{"source":"19","target":"20","data":{}},{"source":"20","target":"21","data":{}},{"source":"24","target":"25","data":{}},{"source":"28","target":"31","data":{}},{"source":"31","target":"29","data":{}},{"source":"29","target":"30","data":{}},{"source":"38","target":"37","data":{}},{"source":"37","target":"36","data":{}},{"source":"42","target":"43","data":{}},{"source":"43","target":"41","data":{}},{"source":"48","target":"49","data":{}},{"source":"49","target":"46","data":{}},{"source":"46","target":"47","data":{}},{"source":"62","target":"65","data":{}},{"source":"65","target":"63","data":{}},{"source":"63","target":"64","data":{}},{"source":"68","target":"70","data":{}},{"source":"70","target":"69","data":{}}]}
let cloneData = {}
onMounted(() => {
  const cy = cytoscape({
    container: document.getElementById('cyto'),
    elements: [
      ...sdmData.nodes.map(node => {
        return {
          data: {
            ...node,
            group: 'node'
          }
        }
      }),
      ...sdmData.edges.map(edge => {
        return {
          data: {
            ...edge,
            group: 'edges'
          }
        }
      })
    ],
    style: [
      {
        selector: 'node',
        style: {
          'label': 'data(name)',
          'text-valign': 'bottom',
          'text-margin-y': 10,
          'text-background-color': '#ffffff',
          'text-background-opacity': 0.5,
          'text-margin-x': 5,
          'background-color': 'cyan',
          'font-size': 15
        }
      },
      {
        selector: 'edge',
        style: {
          'label': 'data(name)',
          'text-valign': 'bottom',
          'text-margin-y': 10,
          'text-background-color': '#ffffff',
          'text-background-opacity': 0.5,
          'text-margin-x': 5,
          "line-color": 'green',
          'target-arrow-color': 'red',
          "target-arrow-shape": 'triangle',
          "curve-style": 'straight',
          'width': 2
        }
      }],
    layout: {
      name: 'klay',
      spacingFactor: 3,
      'randomize': false,
      padding: 5,
    }
  })
  const bb = cy.bubbleSets({ zIndex: 4, throttle: 10, interactive: true})

  cy.one('render', () => {
    let temp = []
    cy.nodes().forEach(node => {
      cloneData[node.id()] = { data: node.outgoers(), collapse: true }
      if (node.incomers().length == 0) temp.push(node)
    })
    cy.remove('*')
    temp.forEach(node => cy.add(node))
  })

  cy.nodes().on('tap', event => {
    if (cloneData[event.target.id()].collapse){ 
      cy.add(cloneData[event.target.id()].data)
      bb.addPath(event.target.successors().nodes(),event.target.successors().edges(),null,{
          virtualEdges: true,
          style: {
            fill: 'rgba(70, 130, 180, 0.4)',
            stroke: 'steelblue',
          },
        })
    }
    else {
      bb.removePath(event.target.successors().nodes(),event.target.successors().edges())
      event.target.successors().nodes().forEach(e => { cloneData[e.id()].collapse = true })
      cy.remove(event.target.successors())
    }
    cloneData[event.target.id()].collapse = !cloneData[event.target.id()].collapse
  })
})
</script>