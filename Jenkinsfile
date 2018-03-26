node {
    stage ("Checkout"){
        def scmVars = checkout scm
        sensediaApiJson "204"
        scmVars.GIT_COMMIT
    }
    stage ("Quality Analyst"){
        sensediaApiQA(destination: true, logInterceptor: true, resourceOutOfSize: true)
    }
    stage ("Deploy hml"){
    	input 'Deploy to Hml?'
        sensediaApiDeploy(enviromentName: "qa")
    }
    stage ("Testes hml"){
        bat "newman run collection_qa.json"
    }
    stage ("Deploy prd"){
    	input 'Deploy to Production?'
        sensediaApiDeploy(enviromentName: "Production")
    }
    stage ("Testes prd"){
        bat "newman run collection_prd.json"
    }
}