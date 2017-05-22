## RPM build instructions

Always `HEAD` version is cloned from the repository. Due to workings
of tagging in mercurial, when requesting a particular tag in archive
command, it has to be one tag ahead the actually wanted one, a special
tag shall always be made before packaging because of this.
	
- `ssh trac.hep.caltech.edu -l maxa`

- `cd ~/rpmbuild/SOURCES`

- `hg -v --debug clone /var/mercurial/fdtcp fdtcp-00-04-04`

- `cd fdtcp-00-04-04`

- `hg archive -r fdtcp-00-04-04-ahead -t tgz ../fdtcp-0.4.4.tgz`
	`fdtcp-00-04-04-ahead` - just a dummy dedicated tag made right
	after `fdtcp-00-04-04` for reasons explained above (one tag ahead `fdtcp-00-04-04`) 

- `cp rpm/fdtcp.rpm.spec ~/rpmbuild/SPECS`

- `cd .. ; rm -fr fdtcp-00-04-04`

- `cd ~/rpmbuild/SPECS`

- edit `fdtcp.rpm.spec` - adjust version, release, changelog ...

- `rpmbuild --buildroot=~/rpmbuild/ -bs --nodeps --define 'dist .el5' fdtcp.rpm.spec`
	(builds source RPM file)
	
- `koji build --scratch dist-el5 ../SRPMS/fdtcp-0.4.4-1.el5.src.rpm` - build with koji scratch
  `koji build dist-el5 ../SRPMS/fdtcp-0.4.4-1.el5.src.rpm` - normal (published) koji build
	
OR	

`rpmbuild -bb --nodeps --define 'dist .el5' ./fdtcp.rpm.spec` - build local RPM without koji


