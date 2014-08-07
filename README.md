if you just want the RPMs





http://mongodb.bauman.in/repo/rpm/mongodb-2.6.3-1.el6.db.x86_64.rpm

http://mongodb.bauman.in/repo/rpm/mongodb-server-2.6.3-1.el6.db.x86_64.rpm

http://mongodb.bauman.in/repo/rpm/mongodb-tools-2.6.3-1.el6.db.x86_64.rpm


http://mongodb.bauman.in/repo/srpms/mongodb-2.6.3-1.el6.db.src.rpm




or keep up to date

    cat > /etc/yum.repos.d/mongodb.bauman.in.repo << EOF
    [mongodb-bauman]
    name=MongoDB for RHEL 6 - x86_64
    baseurl=http://mongodb.bauman.in/repo/
    enabled=1
    gpgcheck=0
    EOF



--------------------------------------------------------



What does it support?


    scons install \

        %{?_smp_mflags} \

        --use-system-snappy \

        --use-system-pcre \

        --prefix=%{buildroot}%{_prefix} \

        --extrapath=%{_prefix} \

        --usev8 \

        --use-system-v8 \

        --nostrip \

        --ssl \

        --use-sasl-client







--------------------------------------------------------

This does not (yet) meet fedora packaging requirements.



TODO Fixes:

* Static link to boost (requires >=1.49 and centos only has 1.41)

* Static link to libstemmer (http://snowball.tartarus.org/download.php, did not package seperately)

* Static link to YAML (requires a 0.5.1)






Did not apply patches:

*   BSON type - this will not work on ARM, but who seriously puts a mongo server on ARM anyway?

*   this misses the atomics optimizatons. 
   


