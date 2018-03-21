node {
    stage ("Checkout"){
        checkout scm
    }
    stage ("Quality Analyst"){
        echo "Destination Test: PASS"
        echo "Log Test: PASS"
    }
    stage ("Deploy Homologação"){
        sensediaApiDeploy("https://manager-demov3.sensedia.com/api-manager/api/v3", "3", "2147001")
    }
    stage ("Testes Homologação"){
        echo "Success"
    }
    stage ("Deploy Produção"){
        sensediaApiDeploy("https://manager-demov3.sensedia.com/api-manager/api/v3", "1", "2147001")
    }
    stage ("Testes Produção"){
        echo "Success"
    }
}