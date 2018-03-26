node {
    stage ("Checkout"){
        checkout scm
        sensediaApiJson "204"
        bat "git.exe add *"
        bat "git.exe commit --no-edit -m 'Automated deploy'"
        bat "git.exe push origin master"
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