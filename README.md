# ArgoCD-Practice

gaming input:
url -X POST http://127.0.0.1:8080/play -H "Content-Type: application/json" -d '{"player":"reddy","guess":9}'
stage('Artifact') {
    steps {
        s3Upload(
            profileName: 'jenkins',

            entries: [[
                sourceFile: 'target/*.war',
                excludedFile: '',
                bucket: 'jenkins-artifact-storage-reddykm',
                storageClass: 'STANDARD',
                selectedRegion: 'us-west-1',
                noUploadOnFailure: true,
                uploadFromSlave: false,
                managedArtifacts: false,
                useServerSideEncryption: false,
                flatten: true,
                gzipFiles: false,
                keepForever: false,
                showDirectlyInBrowser: false,
                userMetadata: []
            ]],

            userMetadata: [],
            dontWaitForConcurrentBuildCompletion: false,
            consoleLogLevel: 'INFO',
            pluginFailureResultConstraint: 'FAILURE',
            dontSetBuildResultOnFailure: false
        )
    }
}
