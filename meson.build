project('gmp-droid', 'c', 'cpp',
  version : '0.1',
  default_options : [ 'warning_level=1',
                      'buildtype=debugoptimized' ])

gmpdroid_version = meson.project_version()
gmpdroid_name = meson.project_name()

cc = meson.get_compiler('c')

root_dir = include_directories('.')
gmp_api = include_directories('gmp-api')
droidmedia_h = include_directories('/usr/include/droidmedia')
hybris_dep = cc.find_library('hybris-common', required: true)

gmpdroid_install_dir = '/'.join([ get_option('libdir'), meson.project_name(), meson.project_version()])

gmp_source = [
  'gmp-droid.cpp',
  'gmp-droid-conv.cpp',
  '/usr/share/droidmedia/hybris.c',
  'gmp-task-utils.h',
  'gmp-task-utils-generated.h'
]

gmpdroid_lib = shared_library('droid',
                       gmp_source,
                       include_directories: [ gmp_api, droidmedia_h ],
                       install: true,
                       dependencies: hybris_dep,
                       install_dir: gmpdroid_install_dir )

info_source = [
  'generate-info.cpp',
  '/usr/share/droidmedia/hybris.c'
]

generate_info = executable('generate-info',
                       info_source,
                       include_directories: [ droidmedia_h ],
                       install: true,
                       dependencies: hybris_dep,
                       install_dir: gmpdroid_install_dir )
