// https://github.com/Rudd-O/shared-jenkins-libraries
@Library('shared-jenkins-libraries@master') _


def srpm_step() {
    return {
        dir('src') {
            script {
                sh (
                script: '''
                ./autogen.sh && ./configure --prefix=/usr && make dist && rpmbuild --define _srcrpmdir" $PWD" -ts *.tar.gz
                ''',
                label: "configure for source RPM"
                )
            }
        }
    }
}


genericFedoraRPMPipeline(
    null,
    srpm_step(),
    ['ncurses-devel', 'lua-devel'],
)
