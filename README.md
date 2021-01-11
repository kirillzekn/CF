# CF
cloud_formation

# Resource

# Parameters
!Ref

# Mappings
!FindInMap

# Outputs
!ImportValue

# GetAttribute
!GetAtt

# Conditions


# CFN-Init
    Metadata:
        AWS::CloudFOrmation::Init:
            config:
            ########################################
                packages:
                    e.g. yum:
                    e.g.    httpd:[]
            ########################################
                groups:
                    e.g. groupABC: {} # any group id
                    e.g. groupDEF:
                        e.g. gid: "45"
            ########################################
                users:
                    myUser:
                        groups:
                            - "groupABC"
                            - "groupDEF"
                        uid: "50"
                        homeDir: "/tmp"
            ########################################
                Sources:
                    /etc/myapp: "http://website.com/archive.zip"
            ########################################
                files:
                    /path/to/file.txt:
                        content: !Sub |
                            file content
                            file content 
                        mode: "000644"
                        owner: "root"
                        group: "root"
            ########################################
                commands:
                    command_name:
                        command: "echo \"$MAGIC\" >text.txt"
                        env:
                            MAGIC: "Hello World"
                        cwd: "~"
                        test: "test ! -e ~/test/txt"
                        ignoreErrors: "false"
            ########################################
                services:
                    sysvinit:
                        httpd:
                            enabled: 'true'
                            ensureRunning: 'true'
            ########################################
# !Sub


# ##################################################### 
# cfn-signal

CreationPolicy:
    ResourceSignal:
        Timeout: PT5M
