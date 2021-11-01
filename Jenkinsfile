timestamps {

	node ('beanstalk') { 

		stage ('my-php-app - Checkout') {
			checkout([$class: 'GitSCM', branches: [[name: '*/main']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'douglasqsantos', url: 'https://github.com/douglasqsantos/my-php-app']]]) 
		}

		stage ('my-php-app - Build') {
				// Shell build step
				sh """ 
				# Initialize the elastic beanstalk app
				# eb platform list --region us-east-2
				eb init my-php-app --platform php-8.0 --region us-east-2

				# Select the development environment for deployment
				eb use Myphpapp-env

				# Deploy the application
				eb deploy

				# Get the health and status information
				eb health
				eb status 
				"""
		}
	}
}
