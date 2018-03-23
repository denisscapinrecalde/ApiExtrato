node {
    stage ("Checkout"){
        checkout scm
    }
    stage ("Quality Analyst"){
        sensediaApiQA(destination: true, logInterceptor: true, resourceOutOfSize: true, resourceSize: 3)
    }
    stage ("Deploy hml"){
    	input 'Deploy to Hml?'
        sensediaApiDeploy(urlManager: "https://manager-demov3.sensedia.com/api-manager/api/v3", managerToken: "ce74056b-efaf-36f7-bdc8-66e4126626e6", enviromentId: "3", revisionId: "2147644")
    }
    stage ("Testes hml"){
        bat "newman run collection.json"
    }
    stage ("Deploy prd"){
    	input 'Deploy to Production?'
        sensediaApiDeploy(urlManager: "https://manager-demov3.sensedia.com/api-manager/api/v3", managerToken: "ce74056b-efaf-36f7-bdc8-66e4126626e6", enviromentId: "1", revisionId: "2147644")
    }
    stage ("Testes prd"){
        bat "newman run collection.json"
    }
}