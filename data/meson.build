subdir('icons')

install_data(
        'io.github.jkozera.ZevDocs.gschema.xml',
        install_dir : join_paths(get_option('prefix'), get_option('datadir'), 'glib-2.0/schemas')
)

libdevhelp_gschema_conf = configuration_data()
libdevhelp_gschema_conf.set('LIBDEVHELP_API_VERSION', LIBDEVHELP_API_VERSION)
configure_file(
        input : 'io.github.jkozera.ZevDocs.gschema.xml.in',
        output : 'io.github.jkozera.ZevDocs-@0@.gschema.xml'.format(LIBDEVHELP_API_VERSION),
        configuration : libdevhelp_gschema_conf,
        install : true,
        install_dir : join_paths(get_option('prefix'), get_option('datadir'), 'glib-2.0/schemas')
)

appdata = 'io.github.jkozera.ZevDocs.appdata.xml'
I18N.merge_file(
        appdata,
        input : appdata + '.in',
        output : appdata,
        po_dir : '../po/',
        install : true,
        install_dir : join_paths(get_option('prefix'), get_option('datadir'), 'metainfo')
)


desktop_file = 'io.github.jkozera.ZevDocs.desktop'
if get_option('snap_build')
        I18N.merge_file(
                desktop_file,
                type : 'desktop',
                input : desktop_file + '.snap.in',
                output : desktop_file,
                po_dir : '../po/',
                install : true,
                install_dir : join_paths(get_option('prefix'), get_option('datadir'), 'applications')
        )
else
        I18N.merge_file(
                desktop_file,
                type : 'desktop',
                input : desktop_file + '.in',
                output : desktop_file,
                po_dir : '../po/',
                install : true,
                install_dir : join_paths(get_option('prefix'), get_option('datadir'), 'applications')
        )

        service_file = 'io.github.jkozera.ZevDocs.service'
        service_conf = configuration_data()
        service_conf.set('bindir', join_paths(get_option('prefix'), get_option('bindir')))
        configure_file(
                input : service_file + '.in',
                output : service_file,
                configuration : service_conf,
                install : true,
                install_dir : join_paths(get_option('prefix'), get_option('datadir'), 'dbus-1/services')
        )
endif

install_data(
        ['assistant.css', 'assistant.js'],
        install_dir : join_paths(get_option('prefix'), get_option('datadir'), 'devhelp/assistant')
)

install_data(
        'devhelp.1',
        install_dir : join_paths(get_option('prefix'), get_option('mandir'), 'man1')
)
