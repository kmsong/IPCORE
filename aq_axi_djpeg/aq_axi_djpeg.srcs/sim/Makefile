iFile			= sample0.jpg
MODEL_PATH		= ../../aq_axi_djpeg.model
fBasename		= $(basename $(notdir $(MODEL_PATH)/$(iFile)))

#$(MAKECMDGOALS) : sim
#	@echo $(MAKECMDGOALS)

SIM : GEN_TV
	ncverilog -f sim.f \
	+defparam+tb_aq_djpeg.sBasenameMem="$(fBasename).mem" \
	+defparam+tb_aq_djpeg.sBasenameLog="$(fBasename).log" \
	+defparam+tb_aq_djpeg.sBasenameDat="$(fBasename).dat"
	$(MODEL_PATH)/convsim $(fBasename).dat $(fBasename).bmp
	+display $(fBasename).bmp &

GEN_TV :
	gcc -o $(MODEL_PATH)/convbtoh $(MODEL_PATH)/convbtoh.c
	$(MODEL_PATH)/convbtoh $(MODEL_PATH)/$(iFile) $(fBasename).mem
	+display $(MODEL_PATH)/$(iFile) &

