Paradigms
=========

Client Storage
==============
seq of lab holders (who they think owns the labs)
LAB HELD
queue listing clients waiting for lab (the lab we hold)

Functions
=========

other.acceptOwnership lab queue
	other.isFinished = false;
	adds itself as holder of lab
	informs the others in queue that it is now the holder
	cancel requests for other labs (by using lab holders that it knows)
	do the experiment

other.updateHolder lab owner
	updates the table of lab holders

other.addMeToQueue lab me
	if other.ownsLab
		other.isFinished
			me.acceptOwnership lab []
		add the client doing requesting to the queue
	else
		find who they think DOES own the lab
			then do same request on that client.

other.cancelMyRequest lab me
	if other.ownsLab
		remove me from queue
	else
		pass message on to who they think owns it

me.releaseLab
	is there somebody in line?
		if yes: first.acceptOwnership lab remainingQueue
			me.updateHolder lab first
		else
			set a flag to remember I'm done
