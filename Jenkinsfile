node {
    def secrets = [
        [$class: 'VaultSecret', path: 'secret/nodejs', secretValues: [
            [$class: 'VaultSecretValue', envVar: 'secret', vaultKey: 'password']
        ]]
    ]

    def configuration = [
        $class: 'VaultConfiguration',
        vaultUrl: 'http://vault:8200',
        vaultCredentialId: 'vault-github-token'
    ]
    
    wrap([$class: 'VaultBuildWrapper', configuration: configuration, vaultSecrets: secrets]) {
        sh 'echo "Hello World"'
        sh 'echo "The secret fetched from Vault is: $secret"'
        sh '''
            echo "Multiline shell steps works too"
            ls -lah
        '''
    }
}
