# NAME

Alien::OpenCV - Find or build OpenCV computer vision library

# SYNOPSIS

From [ExtUtils::MakeMaker](https://metacpan.org/pod/ExtUtils%3A%3AMakeMaker):

    use ExtUtils::MakeMaker;
    use Alien::Base::Wrapper ();

    WriteMakefile(
      Alien::Base::Wrapper->new('Alien::OpenCV')->mm_args2(
        NAME => 'FOO::XS',
        ...
      ),
    );

From [Module::Build](https://metacpan.org/pod/Module%3A%3ABuild):

    use Module::Build;
    use Alien::Base::Wrapper qw( Alien::OpenCV !export );
    use Alien::OpenCV;

    my $build = Module::Build->new(
      ...
      configure_requires => {
        'Alien::Base::Wrapper' => '0',
        'Alien::OpenCV' => '0',
        ...
      },
      Alien::Base::Wrapper->mb_args,
      ...
    );

    $build->create_build_script;

From [Inline::C](https://metacpan.org/pod/Inline%3A%3AC) / [Inline::CPP](https://metacpan.org/pod/Inline%3A%3ACPP) script:

    use Inline 0.56 with => 'Alien::OpenCV';

From [Dist::Zilla](https://metacpan.org/pod/Dist%3A%3AZilla)

    [@Filter]
    -bundle = @Basic
    -remove = MakeMaker

    [Prereqs / ConfigureRequires]
    Alien::OpenCV = 0

    [MakeMaker::Awesome]
    header = use Alien::Base::Wrapper qw( Alien::OpenCV !export );
    WriteMakefile_arg = Alien::Base::Wrapper->mm_args

From [FFI::Platypus](https://metacpan.org/pod/FFI%3A%3APlatypus):

    use FFI::Platypus;
    use Alien::OpenCV;

    my $ffi = FFI::Platypus->new(
      lib => [ Alien::OpenCV->dynamic_libs ],
    );

# DESCRIPTION

This distribution provides OpenCV so that it can be used by other
Perl distributions that are on CPAN.  It does this by first trying to
detect an existing install of OpenCV on your system.  If found it
will use that.  If it cannot be found, the source code will be downloaded
from the internet and it will be installed in a private share location
for the use of other modules.

# SEE ALSO

- [OpenCV](https://opencv.org/)

    The OpenCV home page.

- [Alien](https://metacpan.org/pod/Alien)

    Documentation on the Alien concept itself.

- [Alien::Base](https://metacpan.org/pod/Alien%3A%3ABase)

    The base class for this Alien.

- [Alien::Build::Manual::AlienUser](https://metacpan.org/pod/Alien%3A%3ABuild%3A%3AManual%3A%3AAlienUser)

    Detailed manual for users of Alien classes.
