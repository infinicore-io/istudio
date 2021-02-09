
$topDir = File.expand_path(File.dirname(__FILE__))

def refRootDir(dir)
    return File.join($topDir, dir)
end

desc "Build iStudio"
task :build_istudio do |t, args|
    [
        'yarn',
        'yarn build',
        'yarn build:vscode',
        'yarn release',
        'cd release && yarn --production',
        'yarn release:standalone',
        'yarn package'
    ].each do |cmd|
        system(cmd)
    end
end

