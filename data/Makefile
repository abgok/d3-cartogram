OGR ?= ogr2ogr -F GeoJSON
TOPOJSON ?= ../../topojson/bin/topojson --id-property name
SIMPLIFY ?= 24

all: \
	us-states.topojson \
	us-states-segmentized.topojson
    world.topojson \
    world-segmentized.topojson

us-states-segmentized.geojson: us-states.geojson
	$(OGR) -segmentize 0.5 $@ $<

us-states.topojson: us-states.geojson
	$(TOPOJSON) --simplify $(SIMPLIFY) -o $@ $<
	perl -pi -e "s/us-states/states/g" $@

us-states-segmentized.topojson: us-states-segmentized.geojson
	$(TOPOJSON) -o $@ $<
	perl -pi -e "s/us-states-segmentized/states/g" $@

world.topojson: world.geojson
       $(TOPOJSON) --simplify $(SIMPLIFY) -o $@ $<
       perl -pi -e "s/us-states/states/g" $@

world-segmentized.topojson: world-segmentized.geojson
       $(TOPOJSON) -o $@ $<

clean:
	rm -f us-states-segmentized.geojson
	rm -f *.topojson
