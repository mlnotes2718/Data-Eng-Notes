# Setting Google Cloud SDK CLI in MacOS

**Updated; July 2025**


Please note that this document is based on Google cloud installation instruction with the main focus on Intel MacOS. For updated instructions, always refer to the link below.

Main Reference Link : https://cloud.google.com/sdk/docs/install-sdk

## Prerequisite
- Make sure you created your Google account and have your Google ID ready
- Make sure you created the project using the appropriate name
- Download the correct sdk from the link above.
- Upzip the folder and place into the home directory (In MacOS it is in ~, `cd ~` will bring you to the folder)


## Preparation Before Installation
You could potentially encounter permission issues if the files and folder are not in the correct ownership
Proceed with the following command

```zsh
cd ~
ls -al
```

You could have a list of files and folder similar to the following:
```text
-rw-r--r--  USER     staff   nnn date/time .bash_profile
drwxr-xr-x  USER     staff   nnn date/time .config
-rw-r--r--  USER     staff   nnn date/time .zshrc
drwxr-xr-x  USER     staff   nnn date/time google-cloud-sdk
```
**Make sure the USER is the same as the Mac login. If it is root, you need to change ownership.**

To rectify the permission problem using the following command:
```text
sudo chown -R $USER ~/google-cloud-sdk
sudo chown -R $USER ~/.config
sudo chown -R $USER ~/.zshrc
sudo chown -R $USER ~/.bash_profile
```

## Install SDK
```zsh
./google-cloud-sdk/install.sh
```
**Please not not use sudo.**

If there are no error, we should have the following message:
```text
Welcome to the Google Cloud CLI!

To help improve the quality of this product, we collect anonymized usage data
and anonymized stacktraces when crashes are encountered; additional information
is available at <https://cloud.google.com/sdk/usage-statistics>. This data is
handled in accordance with our privacy policy
<https://cloud.google.com/terms/cloud-privacy-notice>. You may choose to opt in this
collection now (by choosing 'Y' at the below prompt), or at any time in the
future by running the following command:

    gcloud config set disable_usage_reporting false

Do you want to help improve the Google Cloud CLI (y/N)?  N


Your current Google Cloud CLI version is: 513.0.0
The latest available version is: 513.0.0

┌─────────────────────────────────────────────────────────────────────────────────────────────────────────────────┐
│                                                    Components                                                   │
├───────────────┬──────────────────────────────────────────────────────┬──────────────────────────────┬───────────┤
│     Status    │                         Name                         │              ID              │    Size   │
├───────────────┼──────────────────────────────────────────────────────┼──────────────────────────────┼───────────┤
│ Not Installed │ App Engine Go Extensions                             │ app-engine-go                │   4.7 MiB │
│ Not Installed │ Appctl                                               │ appctl                       │  18.5 MiB │
│ Not Installed │ Artifact Registry Go Module Package Helper           │ package-go-module            │   < 1 MiB │
│ Not Installed │ Cloud Bigtable Command Line Tool                     │ cbt                          │  19.3 MiB │
│ Not Installed │ Cloud Bigtable Emulator                              │ bigtable                     │   7.7 MiB │
│ Not Installed │ Cloud Datastore Emulator                             │ cloud-datastore-emulator     │  36.2 MiB │
│ Not Installed │ Cloud Firestore Emulator                             │ cloud-firestore-emulator     │  46.9 MiB │
│ Not Installed │ Cloud Pub/Sub Emulator                               │ pubsub-emulator              │  62.4 MiB │
│ Not Installed │ Cloud Run Proxy                                      │ cloud-run-proxy              │  11.7 MiB │
│ Not Installed │ Cloud SQL Proxy v2                                   │ cloud-sql-proxy              │  13.8 MiB │
│ Not Installed │ Google Container Registry's Docker credential helper │ docker-credential-gcr        │   2.2 MiB │
│ Not Installed │ Kustomize                                            │ kustomize                    │   7.6 MiB │
│ Not Installed │ Log Streaming                                        │ log-streaming                │  16.4 MiB │
│ Not Installed │ Managed Flink Client                                 │ managed-flink-client         │ 383.4 MiB │
│ Not Installed │ Minikube                                             │ minikube                     │  45.2 MiB │
│ Not Installed │ Nomos CLI                                            │ nomos                        │  31.3 MiB │
│ Not Installed │ On-Demand Scanning API extraction helper             │ local-extract                │  23.9 MiB │
│ Not Installed │ Skaffold                                             │ skaffold                     │  35.8 MiB │
│ Not Installed │ Terraform Tools                                      │ terraform-tools              │  66.4 MiB │
│ Not Installed │ anthos-auth                                          │ anthos-auth                  │  21.9 MiB │
│ Not Installed │ config-connector                                     │ config-connector             │  92.7 MiB │
│ Not Installed │ enterprise-certificate-proxy                         │ enterprise-certificate-proxy │   7.9 MiB │
│ Not Installed │ gcloud Alpha Commands                                │ alpha                        │   < 1 MiB │
│ Not Installed │ gcloud Beta Commands                                 │ beta                         │   < 1 MiB │
│ Not Installed │ gcloud app Java Extensions                           │ app-engine-java              │ 128.4 MiB │
│ Not Installed │ gcloud app Python Extensions                         │ app-engine-python            │   3.8 MiB │
│ Not Installed │ gcloud app Python Extensions (Extra Libraries)       │ app-engine-python-extras     │   < 1 MiB │
│ Not Installed │ gke-gcloud-auth-plugin                               │ gke-gcloud-auth-plugin       │   3.5 MiB │
│ Not Installed │ istioctl                                             │ istioctl                     │  28.4 MiB │
│ Not Installed │ kpt                                                  │ kpt                          │  15.4 MiB │
│ Not Installed │ kubectl                                              │ kubectl                      │   < 1 MiB │
│ Not Installed │ kubectl-oidc                                         │ kubectl-oidc                 │  21.9 MiB │
│ Not Installed │ pkg                                                  │ pkg                          │           │
│ Installed     │ BigQuery Command Line Tool                           │ bq                           │   1.8 MiB │
│ Installed     │ Cloud Storage Command Line Tool                      │ gsutil                       │  11.8 MiB │
│ Installed     │ Google Cloud CLI Core Libraries                      │ core                         │  21.0 MiB │
│ Installed     │ Google Cloud CRC32C Hash Tool                        │ gcloud-crc32c                │   1.4 MiB │
└───────────────┴──────────────────────────────────────────────────────┴──────────────────────────────┴───────────┘
To install or remove components at your current SDK version [513.0.0], run:
  $ gcloud components install COMPONENT_ID
  $ gcloud components remove COMPONENT_ID

To update your SDK installation to the latest version [513.0.0], run:
  $ gcloud components update


Modify profile to update your $PATH and enable shell command completion?

Do you want to continue (Y/n)?  Y

The Google Cloud SDK installer will now prompt you to update an rc file to bring
 the Google Cloud CLIs into your environment.

Enter a path to an rc file to update, or leave blank to use 
[/Users/USER/.zshrc]:  
Backing up [/Users/USER/.zshrc] to [/Users/USER/.zshrc.backup].
[/Users/USER/.zshrc] has been updated.

==> Start a new shell for the changes to take effect.


Google Cloud CLI works best with Python 3.12 and certain modules.

Python 3.12 installation detected, install recommended modules? (Y/n)?  Y

Setting up virtual environment
Creating virtualenv...
Installing modules...
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 2.9/2.9 MB 18.6 MB/s eta 0:00:00
Virtual env enabled.

For more information on how to get started, please visit:
  https://cloud.google.com/sdk/docs/quickstarts
```


## Errors During Installation
There are error message as shown below:

```text
Welcome to the Google Cloud CLI!
WARNING: Could not setup log file in /Users/user/.config/gcloud/logs, (PermissionError: [Errno 13] Permission denied: '/Users/user/.config/gcloud/logs/.....log'.
```

or 

```text
Enter a path to an rc file to update, or leave blank to use 
[/Users/USER/.zshrc]:  
Backing up [/Users/USER/.zshrc] to [/Users/USER/.zshrc.backup].
Could not update [/Users/USER/.zshrc]. Ensure you have write access to this location.
```

Make sure you are the owner of the following file or directory:
```text
drwxr-xr-x  20 USER     staff   640 mmm nn nn:nn google-cloud-sdk
```

Make sure you are the owner of the following file or directory:
```text
drwxr-xr-x  20 root     staff   640 mmm nn nn:nn .config
```

For shell configuration file it depends on which shell you are using:
```text
drwxr-xr-x  20 root     staff   640 mmm nn nn:nn .zshrc
drwxr-xr-x  20 root     staff   640 mmm nn nn:nn .bash_profile
```

The owner of the file and folder should be the user Mac login. Having root user will create permission problem:

To rectify the problem:
```text
sudo chown -R $USER ~/google-cloud-sdk
sudo chown -R $USER ~/.config
sudo chown -R $USER ~/.zshrc
sudo chown -R $USER ~/.bash_profile
```
run the following command again

```zsh
./google-cloud-sdk/install.sh
```

You should get similar installation message as above.

Please also check your zshrc file:
```text
# The next line updates PATH for the Google Cloud SDK.
if [ -f '/Users/USER/google-cloud-sdk/path.zsh.inc' ]; then . '/Users/USER/google-cloud-sdk/path.zsh.inc'; fi

# The next line enables shell command completion for gcloud.
if [ -f '/Users/USER/google-cloud-sdk/completion.zsh.inc' ]; then . '/Users/USER/google-cloud-sdk/completion.zsh.inc'; fi
```

## Initialized SDK
Run the following to initialized:
```zsh
./google-cloud-sdk/bin/gcloud init
```

```text
Welcome! This command will take you through the configuration of gcloud.

Your current configuration has been set to: [default]

You can skip diagnostics next time by using the following flag:
  gcloud init --skip-diagnostics

Network diagnostic detects and fixes local network connection issues.
Checking network connection...done.                                            
Reachability Check passed.
Network diagnostic passed (1/1 checks passed).

You must sign in to continue. Would you like to sign in (Y/n)?  

```
At this stage, before you try to enter Y, make sure your default browser is open with the correct google id you want to connect. For multiple ID, please open the browser with the correct google login id.

Then you will bring to a Google login page to login your  Google in and allow permission of teh sdk to access all the necessary items.

When it is done you will be shown the following:

![](google_guide_img/google_cli_done.png)

Then you need to switch to the command prompt:

```text
Your browser has been opened to visit:

    https://accounts.google.com/o/oauth2/auth?response_type...........

You are signed in as: [google-login-id@gmail.com].

Pick cloud project to use: 
 [1] Project1
 [2] Project2
 [3] Enter a project ID
 [4] Create a new project
Please enter numeric choice or text value (must exactly match list item):  2

Your current project has been set to: [Project1].

Not setting default zone/region (this feature makes it easier to use
[gcloud compute] by setting an appropriate default value for the
--zone and --region flag).
See https://cloud.google.com/compute/docs/gcloud-compute section on how to set
default compute region and zone manually. If you would like [gcloud init] to be
able to do this for you the next time you run it, make sure the
Compute Engine API is enabled for your project on the 
https://console.developers.google.com/apis page.

Created a default .boto configuration file at [/Users/USER/.boto]. See this file and
[https://cloud.google.com/storage/docs/gsutil/commands/config] for more
information about configuring Google Cloud Storage.
The Google Cloud CLI is configured and ready to use!

* Commands that require authentication will use machinelearningnotescom@gmail.com by default
* Commands will reference project `project1` by default
Run `gcloud help config` to learn how to change individual settings

This gcloud configuration is called [default]. You can create additional configurations if you work with multiple accounts and/or projects.
Run `gcloud topic configurations` to learn more.

Some things to try next:

* Run `gcloud --help` to see the Cloud Platform services you can interact with. And run `gcloud help COMMAND` to get help on any gcloud command.
* Run `gcloud topic --help` to learn about advanced features of the CLI like arg files and output formatting
* Run `gcloud cheat-sheet` to see a roster of go-to `gcloud` commands.
```

## Enable Login from Application (such as Python)
Need to run the following code:
```zsh
gcloud auth application-default login
```

After going through the login process, you will received the an image similar to the one above when it is successful. **Make sure you check all the boxes.**

Next switch back to your terminal.

```text
Your browser has been opened to visit:

    https://accounts.google.com/o/oauth2/auth.....

Credentials saved to file: [/Users/USER/.config/gcloud/application_default_credentials.json]

These credentials will be used by any library that requests Application Default Credentials (ADC).

Quota project "project1" was added to ADC which can be used by Google client libraries for billing and quota. Note that some services may still bill the project owning the resource.
```

### Connecting Google Storage

In Python file, please include your project name.
```python
from google.cloud import storage
client = storage.Client(project='project-name')
```

Please note that with `gcloud auth application-default login` setup, you will have no issue when linking DBT with Google Bigquery.

# Managing Multiple Projects
The following is my important discovery:

- **If you create a new Google project, you need to rerun `gcloud init` to add the new project.**

To manage between projects please use the following command:
- List all available project: `gcloud projects list`
- Switch to another project: `gcloud config set project PROJECT_ID`
- Confirm the current project: `gcloud config get-value project`
- You may need to reset the quota and billing after switching to a new project: `gcloud auth application-default set-quota-project CURRENT-PROJECT`

For additional command, please refer to the link below:
Reference (Gemini): https://g.co/gemini/share/17505236df87

# Bigquery API Access and Service Key
For integration between various application, you may need to enabled Bigquery API and get the service key. The following are instructions to setup service ket for dbt and meltano.


## Create a New Project
This is optional, however if you want to isolate the resource, you may create a new project. When you create a google cloud login, a new project will automatically created for you. To access projects, please look for the top row for the screen:

![alt text](google_guide_img/project-access.png)

Click on the project, a screen pop-out allows you either to switch to another project or create a new project.

![alt text](google_guide_img/select-project.png)

Click to create a new project

![alt text](google_guide_img/create-project.png)

Click done when finish.

## Enable BigQuery API
- Search and locate the API & Services page

![alt text](google_guide_img/API_Services.png)

- Search for BigQuery API

![alt text](google_guide_img/enable-api.png)

- Enable the API and we are Done.

- To disable the API we can always look for the BiqQuery API and click `Disable` as shown below.

![google_guide_img/diable-API.png](google_guide_img/diable-API.png)


## Bigquery Credentials for dbt
For anything related to Bigquery, you can use the link: https://console.cloud.google.com/bigquery. From here, you can create your dataset or look for Bigquery public dataset.

To create Bigquery credential for dbt, you can either follow the steps below or you can refer to this link https://docs.getdbt.com/guides/bigquery?step=4 from dbt. 

Step 1: Enable Bigquery API and Create Service Account
- Click the link to start Bigquery credential wizard: https://console.cloud.google.com/apis/credentials/wizard

![alt text](google_guide_img/bigquery-dbt.png)

- Select `Bigquery API` and checked `Application data`
- Click `Next`. **IMPORTANT: Do not click Done.**
- You will be given an screen to create a service account for dbt as shown below:

![alt text](google_guide_img/service-account-create.png)

- Set your service account name and click `Create and Continue`. You will be given a screen below to set roles.

![alt text](google_guide_img/set-roles.png)

- Please note that the roles will be different for different application. For dbt, use the following roles:

![alt text](google_guide_img/dbt-roles.png)

- Click `Continue`

![alt text](google_guide_img/click-done.png)

- Now, we can leave the user access as default and click `Done`.

Step 2: Create Service Key
- Click the link https://console.cloud.google.com/iam-admin/serviceaccounts to access service account.
- Select a project you want to manage. You will be given a service account information which you created previously.

![alt text](google_guide_img/service_account.png)

- Click the additional menu under actions

![alt text](google_guide_img/manage-key.png)

- Under actions, select `Manage Key`

![alt text](google_guide_img/add-key.png)

- Click `Add Key`

![alt text](google_guide_img/create_or_upload_key.png)

- Select `Create new key`

![alt text](google_guide_img/select_key_type.png)

- Select `JSON` as the key type and click `Create`.

- A message will be shown as follows, at the same time a key has been created for you and downloaded to your folder:

![alt text](google_guide_img/key_created.png)

For dbt in a local machine (Mac User), it is advisable to place the service key in the folder `/Users/USER/.dbt/`. For production environment, please place it in a secure location and only allow the dbt system access.

## Bigquery Credentials for target-meltano
For meltano, there is no instruction to create service ket, but in our lesson, we where told to create a service account with `BigQuery Admin` role and create a service key.

- We restart from Step 1 shown above. Then we will be given a screen to either use the existing service account or create another one.

![alt text](google_guide_img/2nd-service-account.png)

- Click `Continue` to create another service account.

![alt text](google_guide_img/meltano-service-account.png)

- Enter the name of meltano service account.

![alt text](google_guide_img/meltano-role.png)

- Select the meltano role as shown above.

Then proceed to create another service key for meltano.

For a more restricted access you can grant: role/BigQuery Data Editor, role/BigQuery Job User

Note: To grant additional access, copy the service account email and **Proceed to IAM page (NOT Service Account Page)** to grant additional access.


### Additional Reference 
The following are additional notes on managing the services keys:
- https://cloud.google.com/iam/docs/keys-create-delete
- https://cloud.google.com/iam/docs/best-practices-service-accounts
- https://cloud.google.com/python/docs/reference/bigquery/latest/index.html
