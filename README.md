CREATE TABLE public.countries
(
    name character varying(20) COLLATE pg_catalog."default",
    latitude integer,
    longitude integer,
    area integer,
    population bigint,
    gdp bigint,
    gdpyear integer
)
WITH (
    OIDS = FALSE
)
TABLESPACE pg_default;

ALTER TABLE public.countries
    OWNER to raparici;

CREATE TABLE public.border
(
    name character varying(20) COLLATE pg_catalog."default",
    bordercountry character varying(20) COLLATE pg_catalog."default"
)
WITH (
    OIDS = FALSE
)
TABLESPACE pg_default;

ALTER TABLE public.border
    OWNER to postgres;

INSERT INTO public.countries
	VALUES ('Germany', 51.00, 9.00, 357022, 80594017, 3495000000000, 2016)
INSERT INTO public.countries
    VALUES ('Netherlands', 52.30, 5.45, 41543, 17084719, 773900000000, 2016)
INSERT INTO public.countries
    VALUES ('Belgium', 50.50, 4.00, 30528, 11491346, 470200000000, 2016)
INSERT INTO public.countries
    VALUES ('Luxembourg', 49.45, 6.10, 2586, 594130, 60980000000, 2016)
INSERT INTO public.countries
    VALUES ('Poland', 52.00, 20.00, 312685, 38476269, 467400000000, 2016)
INSERT INTO public.countries
    VALUES ('Czechia', 49.45, 15.30, 78867, 10674723, 193500000000, 2016)
INSERT INTO public.countries
    VALUES ('Austria', 47.20, 13.20, 83871, 8754413, 387300000000, 2016)
INSERT INTO public.countries
    VALUES ('France', 46.00, 2.00, 643801, 67106161, 2488000000000, 2016)
INSERT INTO public.countries
    VALUES ('Switzerland', 47.00, 8.00, 41277, 8236303, 662500000000, 2016);
    
   
INSERT INTO public.boarder VALUES (Germany, Netherlands)
INSERT INTO public.boarder VALUES (Germany, Belgium)
INSERT INTO public.boarder VALUES (Germany, Luxemburg)
INSERT INTO public.boarder VALUES (Germany, Poland)
INSERT INTO public.boarder VALUES (Germany, Czechia)
INSERT INTO public.boarder VALUES (Germany, Austria)
INSERT INTO public.boarder VALUES (Germany, France)
INSERT INTO public.boarder VALUES (Germany, Switzerland);

SELECT * FROM public.border;
SELECT border.bordercountry
FROM public.border
WHERE name = 'Germany';

SELECT * FROM public.countries;
SELECT name
FROM public.countries
WHERE population > 35000000;

SELECT countries.name, border.bordercountry
FROM countries, Border
WHERE countries.population > 35000000 AND border.name = 'Germany';

