node {
    stage ("Checkout"){
        checkout scm
    }
    stage ("Quality Analyst"){
        sensediaApiQA(destination: true)
    }
    stage ("Deploy hml"){
    	input 'Deploy to Hml?'
        sensediaApiDeploy(urlManager: "https://manager-demov3.sensedia.com/api-manager/api/v3", managerToken: "ce74056b-efaf-36f7-bdc8-66e4126626e6", enviromentName: "qa")
    }
    stage ("Testes hml"){
        bat "newman run collection_qa.json"
    }
    stage ("Deploy prd"){
    	input 'Deploy to Production?'
        sensediaApiDeploy(urlManager: "https://manager-demov3.sensedia.com/api-manager/api/v3", managerToken: "ce74056b-efaf-36f7-bdc8-66e4126626e6", enviromentName: "Production")
    }
    stage ("Testes prd"){
        bat "newman run collection_prd.json"
    }
}