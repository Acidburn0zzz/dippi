project('com.github.cassidyjames.dippi', 'vala', 'c')

gnome = import('gnome')
i18n = import('i18n')

add_global_arguments('-DGETTEXT_PACKAGE="@0@"'.format (meson.project_name()), language:'c')

asresources = gnome.compile_resources(
  'as-resources', 'data/' + meson.project_name() + '.gresource.xml',
  source_dir: 'data',
  c_name: 'as'
)

executable(
  meson.project_name(),
  'src/Application.vala',
  'src/MainWindow.vala',
  asresources,
  dependencies: [
    dependency('glib-2.0'),
    dependency('granite'),
    dependency('gtk+-3.0'),
    meson.get_compiler('c').find_library('m', required : false)
  ],
  install: true
)
subdir('data')
subdir('po')

meson.add_install_script('meson/post_install.py')
