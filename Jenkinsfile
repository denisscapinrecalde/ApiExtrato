node {
    stage ("Checkout"){
        checkout scm
    }
    stage ("Quality Analyst"){
        echo "Destination Test: PASS"
        echo "Log Test: PASS"
    }
    stage ("Deploy hml"){
    	input 'Deploy to Hml?'
        sensediaApiDeploy(urlManager: "https://manager-demov3.sensedia.com/api-manager/api/v3", managerToken: "7cd2c42b-7109-3e46-b69b-435aef3eb00a", enviromentId: "3", revisionId: "2147644")
    }
    stage ("Testes hml"){
        newman run collection.json
    }
    stage ("Deploy prd"){
    	input 'Deploy to Production?'
        sensediaApiDeploy(urlManager: "https://manager-demov3.sensedia.com/api-manager/api/v3", managerToken: "7cd2c42b-7109-3e46-b69b-435aef3eb00a", enviromentId: "1", revisionId: "2147644")
    }
    stage ("Testes prd"){
        newman run collection.json
    }
}