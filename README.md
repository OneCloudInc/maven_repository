# maven_repository

OneCloud internal Java Maven Repository

## Instructions

### Prerequisites
1. Make sure you have a GitHub personal access token setup on your machine with access to read/write packages. If you do not, follow the instructions [here](https://help.github.com/en/github/authenticating-to-github/creating-a-personal-access-token-for-the-command-line)
1. Add the generated token to your `~/.zshrc` (or equivalent) as an environment variable `GITHUB_TOKEN`
   1. The token must have access to read/write packages
1. Add another environment variable to your `~/.zshrc` (or equivalent) containing your github username, stored in `GITHUB_USERNAME`

### Publishing Steps

1.  Copy the contents of the sample build.gradle file to your library. then add additional gradle settings and dependencies as desired
1.  Copy the sample gradle.properties file in this repo and replace the variables with the desired values
1.  Develop your library
1.  `./gradlew publish`
1. Once completed, you will see the new package [here](https://github.com/OneCloudInc/maven_repository/packages)

### Using Published Libraries
1. In your `build.gradle` file, add the below maven repository configuration
```groovy
repositories {
    // ... other repositories such as mavenCentral()
    maven {
        url = "https://maven.pkg.github.com/OneCloudInc/maven_repository"
        credentials {
            username = System.getenv("GITHUB_USERNAME")
            password = System.getenv("GITHUB_TOKEN")
        }
    }
}
```
