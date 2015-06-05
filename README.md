# Mozilla-Mork
Mozilla::Mork - Perl extension for reading Mork hash database file such as are used in the Mozilla Address Book and History files.

# Usage

	use Mozilla::Mork;
	$file = $ARGV[0];
	unless ($file) { die "Useage: $0 <filename>\n"; }
	#get a reference to an array of hash's
	my $MorkDetails = Mozilla::Mork->new($file);
	my $results = $MorkDetails->ReturnReferenceStructure();

	# length of the database
	$length = scalar @$results;
	print "Nb items: $length\n";

	# for each email in the database
	for (my $i=0; $i < $length; $i++) {
		my $record = $results->[$i];
		my $flags = @$record{'flags'};

		# printing all fields
		foreach $key (sort (keys($record))) {
			print "$key \t\t@$record{$key}\n";
		}
	}
