project('test', 'cpp')

qt5_mod = import('qt5')

sevenz = find_program('7z', required : true)

zip_file = custom_target('zipfile',
  input : 'test.txt',
  output : 'test.zip',
  command : [sevenz, 'a', '@OUTPUT@', '@INPUT@'],
)

cfg = configuration_data()
cfg.set('PATH', zip_file.full_path())

qrc_file = configure_file(
  configuration : cfg,
  input : 'test.qrc.meson.in',
  output : 'test.qrc',
)

processed = qt5_mod.preprocess(
  qresources : qrc_file,
)

executable('main',
  sources: processed + ['main.cpp'],
  dependencies : dependency('qt5', modules : ['Core'])
)
