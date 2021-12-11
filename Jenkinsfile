// https://github.com/Rudd-O/shared-jenkins-libraries
@Library('shared-jenkins-libraries@master') _

genericFedoraRPMPipeline()


def srpm_step() {
    return {
        dir('src') {
            script {
                sh (
                script: """
                ./autogen.sh && ./configure --prefix=/usr && make dist && rpmbuild -ts *.tar.gz
                rpmbuild -bs 
                """,
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
