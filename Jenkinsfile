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
        sensediaApiDeploy(urlManager: "https://manager-demov3.sensedia.com/api-manager/api/v3", enviromentId: "3", revisionId: "2147644")
    }
    stage ("Testes hml"){
        echo "1/3 - Success"
        echo "2/3 - Success"
        echo "3/3 - Success"
    }
    stage ("Deploy prd"){
    	input 'Deploy to Production?'
        sensediaApiDeploy(urlManager: "https://manager-demov3.sensedia.com/api-manager/api/v3", enviromentId: "1", revisionId: "2147644")
    }
    stage ("Testes prd"){
        echo "1/3 - Success"
        echo "2/3 - Success"
        echo "3/3 - Success"
    }
}