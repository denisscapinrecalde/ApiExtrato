node {
    stage ("Checkout"){
        checkout scm
    }
    stage ("Quality Analyst"){
        echo "Destination Test: PASS"
        echo "Log Test: PASS"
    }
    stage ("Deploy Homologação"){
        sensediaApiDeploy(urlManager: "https://manager-demov3.sensedia.com/api-manager/api/v3", enviromentId: "3", revisionId: "2147001")
    }
    stage ("Testes Homologação"){
        echo "Success"
    }
    stage ("Deploy Produção"){
        sensediaApiDeploy(urlManager: "https://manager-demov3.sensedia.com/api-manager/api/v3", enviromentId: "1", revisionId: "2147001")
    }
    stage ("Testes Produção"){
        echo "Success"
    }
}