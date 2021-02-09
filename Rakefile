require_relative "../gems/build/build_utils"

include ICNBuildUtils

currDir = File.expand_path(File.dirname(__FILE__))

def refRootDir(dir)
    return File.join(currDir, dir)
end

desc "Build vscode-drawio extension"
task :buildDrawIOExt do |t, args|
    drawIODir = File.join(currDir, "lib", "vscode", "extensions", "vscode-drawio")
    if !File.exists?(drawIODir)
        raise "Dir #{drawIODir} does not exists"
    end
    buildTarget = File.join(drawIODir, 'vscode-drawio.vsix')
    if File.exists?(buildTarget)
        FileUtils.rm_f(buildTarget)
    end
    doCmd("cd #{drawIODir} && npm run-script build")
    if !File.exists?(buildTarget)
        raise "Build DrawIO Extension failed: #{buildTarget} not generated"
    end
end

desc "Build iStudio"
task :buildIStudio do |t, args|
    [
        'yarn',
        'yarn build',
        'yarn build:vscode',
        'yarn release',
        'cd release && yarn --production',
        'yarn release:standalone',
    ].each do |cmd|
        system(cmd)
    end
end

desc "Build"
task :build=>[:buildDrawIOExt, :buildIStudio] do |t, args|
end

