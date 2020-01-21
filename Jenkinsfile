pipeline {
    agent { label 'master' }
	options { skipDefaultCheckout() }	
    stages {
                    		stage("Checkout SCM") {
						steps {
								cleanWs()
								echo 'checkout scm'
								checkout scm
						}
				}
				stage("Unit Test") {
					agent { label 'windows' }
						steps {
								cleanWs()
								checkout scm
								echo ' Unit Test Stage'
								bat 'mvn test'
								junit 'target\\surefire-reports\\*.xml'	
						}
				}
	    			/*stage('Scanning for Security') {
					 steps {
						fodStaticAssessment bsiToken: 'eyJ0ZW5hbnRJZCI6OTkyNCwidGVuYW50Q29kZSI6IkRYQ18xODAxX0ZNQV85MjY4ODYyMzciLCJyZWxlYXNlSWQiOjgyMTgyLCJwYXlsb2FkVHlwZSI6IkFOQUxZU0lTX1BBWUxPQUQiLCJhc3Nlc3NtZW50VHlwZUlkIjoxNCwidGVjaG5vbG9neVR5cGUiOiJKQVZBL0oyRUUiLCJ0ZWNobm9sb2d5VHlwZUlkIjo3LCJ0ZWNobm9sb2d5VmVyc2lvbiI6IjEuOCIsInRlY2hub2xvZ3lWZXJzaW9uSWQiOjEyLCJhdWRpdFByZWZlcmVuY2UiOiJBdXRvbWF0ZWQiLCJhdWRpdFByZWZlcmVuY2VJZCI6MiwiaW5jbHVkZVRoaXJkUGFydHkiOmZhbHNlLCJpbmNsdWRlT3BlblNvdXJjZUFuYWx5c2lzIjpmYWxzZSwicG9ydGFsVXJpIjoiaHR0cHM6Ly90cmlhbC5mb3J0aWZ5LmNvbS8iLCJhcGlVcmkiOiJodHRwczovL2FwaS50cmlhbC5mb3J0aWZ5LmNvbSIsInNjYW5QcmVmZXJlbmNlIjoiU3RhbmRhcmQiLCJzY2FuUHJlZmVyZW5jZUlkIjoxfQ==', entitlementPreference: 'SingleScanOnly', inProgressScanActionType: 'CancelInProgressScan', overrideGlobalConfig: true, personalAccessToken: 'fortifyondemand', remediationScanPreferenceType: 'RemediationScanIfAvailable', srcLocation: '.', tenantId: 'DXC_1801_FMA_926886237', username: 'tonisundhp@gmail.com'
						fodPollResults bsiToken: 'eyJ0ZW5hbnRJZCI6OTkyNCwidGVuYW50Q29kZSI6IkRYQ18xODAxX0ZNQV85MjY4ODYyMzciLCJyZWxlYXNlSWQiOjgyMTgyLCJwYXlsb2FkVHlwZSI6IkFOQUxZU0lTX1BBWUxPQUQiLCJhc3Nlc3NtZW50VHlwZUlkIjoxNCwidGVjaG5vbG9neVR5cGUiOiJKQVZBL0oyRUUiLCJ0ZWNobm9sb2d5VHlwZUlkIjo3LCJ0ZWNobm9sb2d5VmVyc2lvbiI6IjEuOCIsInRlY2hub2xvZ3lWZXJzaW9uSWQiOjEyLCJhdWRpdFByZWZlcmVuY2UiOiJBdXRvbWF0ZWQiLCJhdWRpdFByZWZlcmVuY2VJZCI6MiwiaW5jbHVkZVRoaXJkUGFydHkiOmZhbHNlLCJpbmNsdWRlT3BlblNvdXJjZUFuYWx5c2lzIjpmYWxzZSwicG9ydGFsVXJpIjoiaHR0cHM6Ly90cmlhbC5mb3J0aWZ5LmNvbS8iLCJhcGlVcmkiOiJodHRwczovL2FwaS50cmlhbC5mb3J0aWZ5LmNvbSIsInNjYW5QcmVmZXJlbmNlIjoiU3RhbmRhcmQiLCJzY2FuUHJlZmVyZW5jZUlkIjoxfQ==', overrideGlobalConfig: true, personalAccessToken: 'fortifyondemand', pollingInterval: 1, tenantId: 'DXC_1801_FMA_926886237', username: 'tonisundhp@gmail.com'
					}
				}*/
				stage('Build and Package') {
						steps {
								echo 'Clean Build'
								sh "ls"
								sh "pwd"
								sh "mvn sonar:sonar clean compile package -Dtest=\\!TestRunner* -DfailIfNoTests=false -Dsonar.projectKey=addressbook -Dsonar.host.url=http://10.62.125.9:8085/ -Dsonar.login=f16fabd2605044f38e79e4c0e4bc5f73c55dd144"
								//sh "mvn sonar:sonar clean compile -Dtest=\\!TestRunner* -DfailIfNoTests=false -Dsonar.projectKey=employee_jdbc -Dsonar.host.url=http://34.93.123.206/ -Dsonar.login=aac7cc7809ddc82ce0070e3f74726c71216936b6"
								//sh 'mvn clean compile' 
						}
				}
	
				/*stage('Scanning for Security') {
					 steps {
						fodStaticAssessment bsiToken: 'eyJ0ZW5hbnRJZCI6OTY5MywidGVuYW50Q29kZSI6IlZpcnR1c2FfMzQyX0ZNQV8zMjk5MzUyMDYiLCJyZWxlYXNlSWQiOjgwMjIyLCJwYXlsb2FkVHlwZSI6IkFOQUxZU0lTX1BBWUxPQUQiLCJhc3Nlc3NtZW50VHlwZUlkIjoxNCwidGVjaG5vbG9neVR5cGUiOiJKQVZBL0oyRUUiLCJ0ZWNobm9sb2d5VHlwZUlkIjo3LCJ0ZWNobm9sb2d5VmVyc2lvbiI6IjEuNyIsInRlY2hub2xvZ3lWZXJzaW9uSWQiOjEwLCJhdWRpdFByZWZlcmVuY2UiOiJBdXRvbWF0ZWQiLCJhdWRpdFByZWZlcmVuY2VJZCI6MiwiaW5jbHVkZVRoaXJkUGFydHkiOmZhbHNlLCJpbmNsdWRlT3BlblNvdXJjZUFuYWx5c2lzIjpmYWxzZSwicG9ydGFsVXJpIjoiaHR0cHM6Ly90cmlhbC5mb3J0aWZ5LmNvbS8iLCJhcGlVcmkiOiJodHRwczovL2FwaS50cmlhbC5mb3J0aWZ5LmNvbSIsInNjYW5QcmVmZXJlbmNlIjoiU3RhbmRhcmQiLCJzY2FuUHJlZmVyZW5jZUlkIjoxfQ==', entitlementPreference: 'SingleScanOnly', inProgressScanActionType: 'CancelInProgressScan', overrideGlobalConfig: true, personalAccessToken: 'fortifyondemand', remediationScanPreferenceType: 'RemediationScanIfAvailable', srcLocation: '.', tenantId: 'Virtusa_342_FMA_329935206', username: 'preethkumar.k@gmail.com'
						fodPollResults bsiToken: 'eyJ0ZW5hbnRJZCI6OTY5MywidGVuYW50Q29kZSI6IlZpcnR1c2FfMzQyX0ZNQV8zMjk5MzUyMDYiLCJyZWxlYXNlSWQiOjgwMjIyLCJwYXlsb2FkVHlwZSI6IkFOQUxZU0lTX1BBWUxPQUQiLCJhc3Nlc3NtZW50VHlwZUlkIjoxNCwidGVjaG5vbG9neVR5cGUiOiJKQVZBL0oyRUUiLCJ0ZWNobm9sb2d5VHlwZUlkIjo3LCJ0ZWNobm9sb2d5VmVyc2lvbiI6IjEuNyIsInRlY2hub2xvZ3lWZXJzaW9uSWQiOjEwLCJhdWRpdFByZWZlcmVuY2UiOiJBdXRvbWF0ZWQiLCJhdWRpdFByZWZlcmVuY2VJZCI6MiwiaW5jbHVkZVRoaXJkUGFydHkiOmZhbHNlLCJpbmNsdWRlT3BlblNvdXJjZUFuYWx5c2lzIjpmYWxzZSwicG9ydGFsVXJpIjoiaHR0cHM6Ly90cmlhbC5mb3J0aWZ5LmNvbS8iLCJhcGlVcmkiOiJodHRwczovL2FwaS50cmlhbC5mb3J0aWZ5LmNvbSIsInNjYW5QcmVmZXJlbmNlIjoiU3RhbmRhcmQiLCJzY2FuUHJlZmVyZW5jZUlkIjoxfQ==', overrideGlobalConfig: true, personalAccessToken: 'fortifyondemand', pollingInterval: 1, tenantId: 'Virtusa_342_FMA_329935206', username: 'preethkumar.k@gmail.com'
					}
				}*/  
	
				/*stage('Package') {
					steps {
						echo 'Packaging'
						sh 'mvn package -DskipTests'
					}
				}*/
	    			stage("XLDeploy Package") {
					steps {
						sh "sed -i 's/{{PACKAGE_VERSION}}/$BUILD_NUMBER.0/g' deployit-manifest.xml"
						xldCreatePackage artifactsPath: 'target', manifestPath: 'deployit-manifest.xml', darPath: '$JOB_NAME-$BUILD_NUMBER.0.dar'  
					}
				}
	    			stage('XLDeploy Publish') {  
					steps {
    						xldPublishPackage serverCredentials: 'XLDeployServer', darPath: '$JOB_NAME-$BUILD_NUMBER.0.dar'
					}
				}  
	    			stage('XLDeploy Deploy') { 
					steps {
    						xldDeploy serverCredentials: 'XLDeployServer', environmentId: 'Environments/QATomcatENv', packageId: 'Applications/AddressBook/$BUILD_NUMBER.0'
					}
				}
				/*stage("publish to nexus") {
					steps {
						echo 'publish to nexus'
						script {
							// Read POM xml file using 'readMavenPom' step , this step 'readMavenPom' is included in: https://plugins.jenkins.io/pipeline-utility-steps
							pom = readMavenPom file: "pom.xml";
							// Find built artifact under target folder
							filesByGlob = findFiles(glob: "target/*.${pom.packaging}");
							// Print some info from the artifact found
							echo "${filesByGlob[0].name} ${filesByGlob[0].path} ${filesByGlob[0].directory} ${filesByGlob[0].length} ${filesByGlob[0].lastModified}"
							// Extract the path from the File found
							artifactPath = filesByGlob[0].path;
							// Assign to a boolean response verifying If the artifact name exists
							artifactExists = fileExists artifactPath;
							if(artifactExists) {
								echo "*** File: ${artifactPath}, group: ${pom.groupId}, packaging: ${pom.packaging}, version ${pom.version}";
								nexusArtifactUploader(
									nexusVersion: NEXUS_VERSION,
									protocol: NEXUS_PROTOCOL,
									nexusUrl: NEXUS_URL,
									groupId: pom.groupId,
									version: pom.version,
									repository: NEXUS_REPOSITORY,
									credentialsId: NEXUS_CREDENTIAL_ID,
									artifacts: [
										// Artifact generated such as .jar, .ear and .war files.
										[artifactId: pom.artifactId,
										classifier: '',
										file: artifactPath,
										type: pom.packaging]//,
										// Lets upload the pom.xml file for additional information for Transitive dependencies

									]
								);
							} else {
								error "*** File: ${artifactPath}, could not be found";
							}
							
						}

					}
					post {
							success {
								//junit 'target/surefire-reports/*.xml'
								hygieiaArtifactPublishStep artifactDirectory: 'target', artifactGroup: 'com.addressbook', artifactName: 'addressbook.war', artifactVersion: '2'
								//hygieiaDeployPublishStep applicationName: 'Addressbook', artifactDirectory: 'target', artifactGroup: 'com.addressbook', artifactName: 'addressbook.war', artifactVersion: '2', buildStatus: 'Success', environmentName: 'Dev'
							}
						   failure {
								//junit 'target/surefire-reports/*.xml'
								hygieiaArtifactPublishStep artifactDirectory: 'target', artifactGroup: 'com.addressbook', artifactName: 'addressbook.war', artifactVersion: '2'
								//hygieiaDeployPublishStep applicationName: 'Addressbook', artifactDirectory: 'target', artifactGroup: 'com.addressbook', artifactName: 'addressbook.war', artifactVersion: '2', buildStatus: 'Failure', environmentName: 'Dev'
							
							}
					}
				}*/
				/*stage('Deploy') {
					steps {
						sh 'curl --upload-file target/addressbook.war "http://tomcat:password@10.62.125.4:8083/manager/text/deploy?path=/addressbook&update=true"'
						//sh 'curl --upload-file target/addressbook.war "http://tomcat:password@34.93.238.186:8081/manager/text/deploy?path=/addressbook&update=true"'
						//withCredentials([usernamePassword(credentialsId: 'nexusadmin', passwordVariable: 'pass', usernameVariable: 'user')]) {
						//    sh 'curl --upload-file target/hello-world-war-1.0.0-SNAPSHOT.war "http://${user}:${pass}@34.93.240.217:8082/manager/text/deploy?path=/hello&update=true"'
						//}
					}
				}*/
				/*stage("deploy") {
					steps {
							echo 'deploy artifact from nexus'
							// sh 'cp -arf /home/ubuntu/playbooks/deployment.yml ./deployment.yml'
							ansiColor('xterm') {
								ansiblePlaybook( 
								playbook: 'deploy_nexus.yml',
								credentialsId: 'ansible',
								extras: '-vvv',
								colorized: true) 
							}
					  
						 }
					post {
							success {
								//junit 'target/surefire-reports/*.xml'
								//hygieiaArtifactPublishStep artifactDirectory: 'target', artifactGroup: 'com.addressbook', artifactName: 'addressbook.war', artifactVersion: 'pom.version'
								hygieiaDeployPublishStep applicationName: 'Addressbook', artifactDirectory: 'target', artifactGroup: 'com.addressbook', artifactName: 'addressbook.war', artifactVersion: '2', buildStatus: 'Success', environmentName: 'Dev'
							}
						   failure {
								//junit 'target/surefire-reports/*.xml'
								//hygieiaArtifactPublishStep artifactDirectory: 'target', artifactGroup: 'com.addressbook', artifactName: 'addressbook.war', artifactVersion: 'pom.version'
								hygieiaDeployPublishStep applicationName: 'Addressbook', artifactDirectory: 'target', artifactGroup: 'com.addressbook', artifactName: 'addressbook.war', artifactVersion: '2', buildStatus: 'Failure', environmentName: 'Dev'
							
							}
					}
				}*/
				stage('Test Script Checkout and Execution') {
				   agent { label 'windows' }
					stages {
						stage("Checkout") {
							steps {
								 checkout([  
									$class: 'GitSCM', 
									branches: [[name: 'refs/heads/master']], 
									doGenerateSubmoduleConfigurations: false, 
									extensions: [[$class: 'RelativeTargetDirectory', relativeTargetDir: 'bdd']], 
									submoduleCfg: [], 
									userRemoteConfigs: [[credentialsId: 'rakeshgitvirtusatoken', url: 'https://git.virtusa.com/intelligent-automation/web_bdd.git']]
								])
								checkout([  
									$class: 'GitSCM', 
									branches: [[name: 'refs/heads/master']], 
									doGenerateSubmoduleConfigurations: false, 
									extensions: [[$class: 'RelativeTargetDirectory', relativeTargetDir: 'api']], 
									submoduleCfg: [], 
									userRemoteConfigs: [[credentialsId: 'rakeshgitvirtusatoken', url: 'https://git.virtusa.com/intelligent-automation/api_bdd.git']]
								])
								checkout([  
									$class: 'GitSCM', 
									branches: [[name: 'refs/heads/master']], 
									doGenerateSubmoduleConfigurations: false, 
									extensions: [[$class: 'RelativeTargetDirectory', relativeTargetDir: 'swing']], 
									submoduleCfg: [], 
									userRemoteConfigs: [[credentialsId: 'rakeshgitvirtusatoken', url: 'https://git.virtusa.com/intelligent-automation/swing_bdd.git']]
								])
							} 
						}
		    
						stage("Web Smoke Test") {
							steps {
								dir('bdd') {
												echo 'WEB BDD Testing Stage'
												step([$class: 'XrayExportBuilder', filePath: '\\src\\test\\resource\\features', issues: 'AD-22', serverInstance: 'ce436e2b-0499-443c-9431-1864e5d99242'])
												bat 'mvn test -Dcucumber.options="--tags @smoke"'
												bat 'mkdir ..\\target\\cucumber-reports\\Web-Smoke'
												bat 'copy target\\cucumber-reports\\Cucumber.json ..\\target\\cucumber-reports\\Web-Smoke\\Cucumber-smoke.json'
												step([$class: 'XrayImportBuilder', endpointName: '/cucumber/multipart',importInfo:'''{

													"fields": {
														"project": {
															"id": "10000"
														},
														"summary": "Smoke Web Test Execution for Addressbook BDD (Generated By ${BUILD_TAG})",
														"issuetype": {
															"id": "10007"
														},
												   "labels":["smoke","Jenkins"],
													  
														"customfield_10032" : [
														   "Dev"
														]
													}
												}''',testExecKey:'AD-23',inputInfoSwitcher:"fileContent",importFilePath: '..\\target\\cucumber-reports\\Web-Smoke\\Cucumber-smoke.json', serverInstance: 'ce436e2b-0499-443c-9431-1864e5d99242'])
												//step([$class: 'XrayImportBuilder', endpointName: '/cucumber',importInfo:'''{"fields": {"project": {"id": "10000"},"summary": "Smoke Web Test Execution for Addressbook BDD (Generated By ${BUILD_TAG})","issuetype": {"id": "10007"},"labels":["smoke","Jenkins"],"customfield_10032" : ["Dev"]}}''',inputInfoSwitcher:"fileContent", importFilePath: '\\target\\cucumber-reports\\Cucumber.json', serverInstance: 'ce436e2b-0499-443c-9431-1864e5d99242'])
													
								}
							} 
						}
						stage("API Smoke Test") {
							steps {
								dir('api') {
											echo 'API smoke Testing Stage'
											step([$class: 'XrayExportBuilder', filePath: '\\src\\test\\java\\com\\virtusa\\qa\\api', issues: 'API-5', serverInstance: 'ce436e2b-0499-443c-9431-1864e5d99242'])
											bat 'mvn clean test -Dcucumber.options="--tags @smoke"'
											bat 'mkdir ..\\target\\cucumber-reports\\API-Smoke'
											bat 'copy target\\surefire-reports\\com.virtusa.qa.api.product.json ..\\target\\cucumber-reports\\API-Smoke\\API-smoke.json'
											step([$class: 'XrayImportBuilder', endpointName: '/cucumber/multipart',importInfo:'''{

													"fields": {
														"project": {
															"id": "10100"
														},
														"summary": "Smoke Api Test Execution for BDD (Generated By API Product ${BUILD_NUMBER})",
														"issuetype": {
															"id": "10007"
														},
												   "labels":["smoke","Jenkins","Api"],
													  
														"customfield_10032" : [
														   "Dev"
														]
													}
												}''',inputInfoSwitcher:"fileContent",importFilePath: '\\target\\surefire-reports\\com.virtusa.qa.api.1_API-1.json', serverInstance: 'ce436e2b-0499-443c-9431-1864e5d99242'])
												
								}
							} 
						}
						/*stage("Web Feature Test") {
							steps {
								dir('web') {
								echo 'Testing Stage'
								bat 'mvn test -Dcucumber.option="--tags @feature"'
								bat 'copy target\\cucumber-reports\\Cucumber.json target\\cucumber-reports\\Cucumber-sanity.json'
								bat 'del /f target\\cucumber-reports\\Cucumber.json'
								}
							}
						}
						stage("API Feature Test") {
							steps {
								dir('api') {
									echo 'Testing Stage'
									bat 'mvn test -Dcucumber.option="--tags @feature"'
									bat 'copy target\\surefire-reports\\com.virtusa.qa.api.product.json D:\\workspace\\workspace\\addressbook\\bdd\\target\\cucumber-reports\\API-feature.json'
									bat 'del /f target\\cucumber-reports\\Cucumber.json'
								}
							}
						}*/
						stage("Web Regression Test") {
							steps {
								dir('bdd') {
										echo 'Web regression Testing Stage'
										//step([$class: 'XrayExportBuilder', filePath: '\\src\\test\\resource\\features', issues: 'AD-22', serverInstance: 'ce436e2b-0499-443c-9431-1864e5d99242'])
										bat 'mvn test -Dcucumber.options="--tags @regression"'
									        bat 'mkdir ..\\target\\cucumber-reports\\Web-Regression'
										bat 'copy target\\cucumber-reports\\Cucumber.json ..\\target\\cucumber-reports\\Web-Regression\\Cucumber-regression.json'
										bat 'del /f target\\cucumber-reports\\Cucumber.json'
										step([$class: 'XrayImportBuilder', endpointName: '/cucumber/multipart',importInfo:'''{

											"fields": {
												"project": {
													"id": "10000"
												},
												"summary": "Regression Web Test Execution for Addressbook BDD (Generated By ${BUILD_TAG})",
												"issuetype": {
													"id": "10007"
												},
										   "labels":["Regression","Jenkins"],
											  
												"customfield_10032" : [
												   "Dev"
												]
											}
										}''',inputInfoSwitcher:"fileContent",importFilePath: '..\\target\\cucumber-reports\\Web-Regression\\Cucumber-regression.json', serverInstance: 'ce436e2b-0499-443c-9431-1864e5d99242'])
										//step([$class: 'XrayImportBuilder', endpointName: '/cucumber',importInfo:'''{"fields": {"project": {"id": "10000"},"summary": "Regression Web Test Execution for Addressbook BDD (Generated By ${BUILD_TAG})","issuetype": {"id": "10007"},"labels":["Regression","Jenkins"],"customfield_10032" : ["Dev"]}}''',inputInfoSwitcher:"fileContent", importFilePath: '\\target\\cucumber-reports\\Cucumber-regression.json', serverInstance: 'ce436e2b-0499-443c-9431-1864e5d99242'])
										
										
								}
							}
							
							post {
								always {
									//bat 'xcopy target\\allure-results ..\\allure-results /S /i'
									//bat 'rd /s /q target\\allure-results'	
									allure results: [[path: 'bdd\\target\\allure-results']]

									}
								}
						}
						stage("API Regression Test") {
							steps {
								dir('api') {
									echo 'API API regression Testing Stage'
								  	//step([$class: 'XrayExportBuilder', filePath: '\\src\\test\\java\\com\\virtusa\\qa\\api', issues: 'API-5', serverInstance: 'ce436e2b-0499-443c-9431-1864e5d99242'])

									bat 'mvn clean test -Dcucumber.options="--tags @regression"'
									bat 'mkdir ..\\target\\cucumber-reports\\API-Regression'
									bat 'copy target\\surefire-reports\\com.virtusa.qa.api.product.json ..\\target\\cucumber-reports\\API-Regression\\API-regression.json'
									step([$class: 'XrayImportBuilder', endpointName: '/cucumber/multipart',importInfo:'''{

													"fields": {
														"project": {
															"id": "10100"
														},
														"summary": "Regression Api Test Execution for BDD (Generated By ${BUILD_NUMBER})",
														"issuetype": {
															"id": "10007"
														},
												   "labels":["Regression","Jenkins","Api"],
													  
														"customfield_10032" : [
														   "Dev"
														]
													}
												}''',inputInfoSwitcher:"fileContent",importFilePath: '\\target\\surefire-reports\\com.virtusa.qa.api.1_API-1.json', serverInstance: 'ce436e2b-0499-443c-9431-1864e5d99242'])
												
									bat 'del /f target\\surefire-reports\\com.virtusa.qa.api.product.json'
									bat 'del /f target\\surefire-reports\\com.virtusa.qa.api.1_API-1.json'
								}
							}
						}
		    
						stage("Desktop Test") {
							steps {
								dir('swing') {
									echo 'Testing Desktop'
								    step([$class: 'XrayExportBuilder', filePath: '\\src\\test\\resource\\features', issues: 'SDA-5', serverInstance: 'ce436e2b-0499-443c-9431-1864e5d99242'])
									
									bat 'mvn test'
									bat 'mkdir ..\\target\\cucumber-reports\\Desktop-Test'
									bat 'copy target\\cucumber-reports\\Cucumber.json ..\\target\\cucumber-reports\\Desktop-Test\\Cucumber-desktop.json'
									step([$class: 'XrayImportBuilder', endpointName: '/cucumber/multipart',importInfo:'''{

													"fields": {
														"project": {
															"id": "10101"
														},
														"summary": " Desktop App Test Execution for BDD (Generated By Swing ${BUILD_NUMBER})",
														"issuetype": {
															"id": "10007"
														},
												   "labels":["Desktop","Jenkins"],
													  
														"customfield_10032" : [
														   "Dev"
														]
													}
												}''',inputInfoSwitcher:"fileContent",importFilePath: '..\\target\\cucumber-reports\\Desktop-Test\\Cucumber-desktop.json', serverInstance: 'ce436e2b-0499-443c-9431-1864e5d99242'])
												
									bat 'del /f target\\cucumber-reports\\Cucumber.json'
									//bat 'copy target\\jacoco.exec D:\\workspace\\workspace\\addressbook\\target\\jacoco-web.exec'
							
								}
							}
						}

						/*stage("Jacoco Code Coverage report") {
							steps {
									jacoco(execPattern: '\\target\\*.exec')
							}
						} */
		        
						/*stage("Sanity Test") {
							steps {
								dir('bdd') {
								echo 'Testing Stage'
								bat 'mvn test -Dcucumber.option="--tags @sanity'
								bat 'copy target\\cucumber-reports\\Cucumber.json target\\cucumber-reports\\Cucumber-sanity.json'
								bat 'del /f target\\cucumber-reports\\Cucumber.json'
								}
							}
						}*/
                
						stage("Cucumber Report generation") {
							steps {
								
								cucumber buildStatus: 'UNSTABLE',
									failedFeaturesNumber: 1,
									failedScenariosNumber: 1,
									skippedStepsNumber: 1,
									failedStepsNumber: 1,
									/*classifications: [
											[key: 'Commit', value: '<a href="${GIT_URL_1}">${GIT_COMMIT}</a>'],
											[key: 'Submitter', value: '${GIT_AUTHOR_NAME}']
									],*/
									fileIncludePattern: '**/*.json',
									jsonReportDirectory: 'target\\cucumber-reports',
									sortingMethod: 'ALPHABETICAL',
									trendsLimit: 100   
							}
						post {
							always {
	    							hygieiaTestPublishStep buildStatus: "${currentBuild.currentResult}", testApplicationName: 'addressbook', testEnvironmentName: 'Dev', testFileNamePattern: 'Cucumber-smoke.json', testResultsDirectory: '\\target\\cucumber-reports\\Web-Smoke', testType: 'Functional'
								hygieiaTestPublishStep buildStatus: "${currentBuild.currentResult}", testApplicationName: 'addressbook', testEnvironmentName: 'Dev', testFileNamePattern: 'API-smoke.json', testResultsDirectory: '\\target\\cucumber-reports\\API-Smoke', testType: 'Functional'
								hygieiaTestPublishStep buildStatus: "${currentBuild.currentResult}", testApplicationName: 'addressbook', testEnvironmentName: 'Dev', testFileNamePattern: 'Cucumber-desktop.json', testResultsDirectory: '\\target\\cucumber-reports\\Desktop-Test', testType: 'Functional'
								hygieiaTestPublishStep buildStatus: "${currentBuild.currentResult}", testApplicationName: 'addressbook', testEnvironmentName: 'Dev', testFileNamePattern: 'Cucumber-regression.json', testResultsDirectory: '\\target\\cucumber-reports\\Web-Regression', testType: 'Functional'
								hygieiaTestPublishStep buildStatus: "${currentBuild.currentResult}", testApplicationName: 'addressbook', testEnvironmentName: 'Dev', testFileNamePattern: 'API-regression.json', testResultsDirectory: '\\target\\cucumber-reports\\API-Regression', testType: 'Functional'
							
								}
							}
						}
					}     
				}
	}
    tools {
        maven 'maven3.3.9'
        jdk 'openjdk8'
    }
    environment {
        // This can be nexus3 or nexus2
        NEXUS_VERSION = "nexus3"
        // This can be http or https
        NEXUS_PROTOCOL = "http"
        // Where your Nexus is running
        NEXUS_URL = "10.62.125.9:8084"
        //NEXUS_URL = "35.200.184.59:8081"
        // Repository where we will upload the artifact
        NEXUS_REPOSITORY = "maven-snapshots"
        // Jenkins credential id to authenticate to Nexus OSS
        NEXUS_CREDENTIAL_ID = "nexusadmin"
    }
    
    post {
         always {
            echo 'JENKINS PIPELINE'
	    
        }
        success {
            echo 'JENKINS PIPELINE SUCCESSFUL'
        }
        failure {
            echo 'JENKINS PIPELINE FAILED'
        }
        unstable {
            echo 'JENKINS PIPELINE WAS MARKED AS UNSTABLE'
        }
        changed {
            echo 'JENKINS PIPELINE STATUS HAS CHANGED SINCE LAST EXECUTION'
        }
    }
}
