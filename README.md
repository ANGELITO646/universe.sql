# universe.sql

--
-- PostgreSQL database dump
--

-- Dumped from database version 12.9 (Ubuntu 12.9-2.pgdg20.04+1)
-- Dumped by pg_dump version 12.9 (Ubuntu 12.9-2.pgdg20.04+1)

SET statement_timeout = 0;
SET lock_timeout = 0;
SET idle_in_transaction_session_timeout = 0;
SET client_encoding = 'UTF8';
SET standard_conforming_strings = on;
SELECT pg_catalog.set_config('search_path', '', false);
SET check_function_bodies = false;
SET xmloption = content;
SET client_min_messages = warning;
SET row_security = off;

DROP DATABASE universe;
--
-- Name: universe; Type: DATABASE; Schema: -; Owner: freecodecamp
--

CREATE DATABASE universe WITH TEMPLATE = template0 ENCODING = 'UTF8' LC_COLLATE = 'C.UTF-8' LC_CTYPE = 'C.UTF-8';


ALTER DATABASE universe OWNER TO freecodecamp;

\connect universe

SET statement_timeout = 0;
SET lock_timeout = 0;
SET idle_in_transaction_session_timeout = 0;
SET client_encoding = 'UTF8';
SET standard_conforming_strings = on;
SELECT pg_catalog.set_config('search_path', '', false);
SET check_function_bodies = false;
SET xmloption = content;
SET client_min_messages = warning;
SET row_security = off;

SET default_tablespace = '';

SET default_table_access_method = heap;

--
-- Name: galaxy; Type: TABLE; Schema: public; Owner: freecodecamp
--

CREATE TABLE public.galaxy (
    galaxy_id integer NOT NULL,
    name character varying(50) NOT NULL,
    age_in_million_of_years integer,
    apparent_magnitude integer,
    color character varying(30)
);


ALTER TABLE public.galaxy OWNER TO freecodecamp;

--
-- Name: galaxy_galaxy_id_seq; Type: SEQUENCE; Schema: public; Owner: freecodecamp
--

CREATE SEQUENCE public.galaxy_galaxy_id_seq
    AS integer
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;


ALTER TABLE public.galaxy_galaxy_id_seq OWNER TO freecodecamp;

--
-- Name: galaxy_galaxy_id_seq; Type: SEQUENCE OWNED BY; Schema: public; Owner: freecodecamp
--

ALTER SEQUENCE public.galaxy_galaxy_id_seq OWNED BY public.galaxy.galaxy_id;


--
-- Name: moon; Type: TABLE; Schema: public; Owner: freecodecamp
--

CREATE TABLE public.moon (
    moon_id integer NOT NULL,
    name character varying(50) NOT NULL,
    planet_id integer,
    description text,
    has_life boolean
);


ALTER TABLE public.moon OWNER TO freecodecamp;

--
-- Name: moon_moon_id_seq; Type: SEQUENCE; Schema: public; Owner: freecodecamp
--

CREATE SEQUENCE public.moon_moon_id_seq
    AS integer
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;


ALTER TABLE public.moon_moon_id_seq OWNER TO freecodecamp;

--
-- Name: moon_moon_id_seq; Type: SEQUENCE OWNED BY; Schema: public; Owner: freecodecamp
--

ALTER SEQUENCE public.moon_moon_id_seq OWNED BY public.moon.moon_id;


--
-- Name: planet; Type: TABLE; Schema: public; Owner: freecodecamp
--

CREATE TABLE public.planet (
    planet_id integer NOT NULL,
    name character varying(50) NOT NULL,
    star_id integer,
    distance_from_star_millionkm numeric(9,2),
    has_life boolean
);


ALTER TABLE public.planet OWNER TO freecodecamp;

--
-- Name: planet_planet_id_seq; Type: SEQUENCE; Schema: public; Owner: freecodecamp
--

CREATE SEQUENCE public.planet_planet_id_seq
    AS integer
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;


ALTER TABLE public.planet_planet_id_seq OWNER TO freecodecamp;

--
-- Name: planet_planet_id_seq; Type: SEQUENCE OWNED BY; Schema: public; Owner: freecodecamp
--

ALTER SEQUENCE public.planet_planet_id_seq OWNED BY public.planet.planet_id;


--
-- Name: space_rock; Type: TABLE; Schema: public; Owner: freecodecamp
--

CREATE TABLE public.space_rock (
    space_rock_id integer NOT NULL,
    name character varying(50) NOT NULL,
    age_in_billion_of_years numeric(5,2)
);


ALTER TABLE public.space_rock OWNER TO freecodecamp;

--
-- Name: space_rock_space_rock_id_seq; Type: SEQUENCE; Schema: public; Owner: freecodecamp
--

CREATE SEQUENCE public.space_rock_space_rock_id_seq
    AS integer
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;


ALTER TABLE public.space_rock_space_rock_id_seq OWNER TO freecodecamp;

--
-- Name: space_rock_space_rock_id_seq; Type: SEQUENCE OWNED BY; Schema: public; Owner: freecodecamp
--

ALTER SEQUENCE public.space_rock_space_rock_id_seq OWNED BY public.space_rock.space_rock_id;


--
-- Name: star; Type: TABLE; Schema: public; Owner: freecodecamp
--

CREATE TABLE public.star (
    star_id integer NOT NULL,
    name character varying(50) NOT NULL,
    galaxy_id integer,
    age_in_million_of_years numeric(8,2),
    color character varying(30)
);


ALTER TABLE public.star OWNER TO freecodecamp;

--
-- Name: star_star_id_seq; Type: SEQUENCE; Schema: public; Owner: freecodecamp
--

CREATE SEQUENCE public.star_star_id_seq
    AS integer
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;


ALTER TABLE public.star_star_id_seq OWNER TO freecodecamp;

--
-- Name: star_star_id_seq; Type: SEQUENCE OWNED BY; Schema: public; Owner: freecodecamp
--

ALTER SEQUENCE public.star_star_id_seq OWNED BY public.star.star_id;


--
-- Name: galaxy galaxy_id; Type: DEFAULT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.galaxy ALTER COLUMN galaxy_id SET DEFAULT nextval('public.galaxy_galaxy_id_seq'::regclass);


--
-- Name: moon moon_id; Type: DEFAULT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.moon ALTER COLUMN moon_id SET DEFAULT nextval('public.moon_moon_id_seq'::regclass);


--
-- Name: planet planet_id; Type: DEFAULT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.planet ALTER COLUMN planet_id SET DEFAULT nextval('public.planet_planet_id_seq'::regclass);


--
-- Name: space_rock space_rock_id; Type: DEFAULT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.space_rock ALTER COLUMN space_rock_id SET DEFAULT nextval('public.space_rock_space_rock_id_seq'::regclass);


--
-- Name: star star_id; Type: DEFAULT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.star ALTER COLUMN star_id SET DEFAULT nextval('public.star_star_id_seq'::regclass);


--
-- Data for Name: galaxy; Type: TABLE DATA; Schema: public; Owner: freecodecamp
--

INSERT INTO public.galaxy VALUES (1, 'Milky Way', 14, -7, 'White');
INSERT INTO public.galaxy VALUES (2, 'Large Megallonic Cloud', 1, 1, NULL);
INSERT INTO public.galaxy VALUES (3, 'Small Megallonic Cloud', 7, 3, 'Red-green');
INSERT INTO public.galaxy VALUES (4, 'Andromeda Galaxy', 10, 4, 'Blueshifted');
INSERT INTO public.galaxy VALUES (5, 'Triangulum Galaaxy', 3, 6, 'Blue- and violet-');
INSERT INTO public.galaxy VALUES (6, 'Sculptor Galaxy', 6, 7, NULL);


--
-- Data for Name: moon; Type: TABLE DATA; Schema: public; Owner: freecodecamp
--

INSERT INTO public.moon VALUES (1, 'Luna', 3, 'the fifth largest moon in the solar system', false);
INSERT INTO public.moon VALUES (2, 'Phobos', 4, 'twin brother of Deimos', false);
INSERT INTO public.moon VALUES (3, 'Deimos', 4, 'twin brother of Phobos', false);
INSERT INTO public.moon VALUES (4, 'Ganymede', 5, 'the largest and most massive moon in the Solar System', false);
INSERT INTO public.moon VALUES (5, 'Callisto', 5, 'Jupiters second largest moon and the third largest moon in our solar system', false);
INSERT INTO public.moon VALUES (6, 'Lo', 5, 'the most volcanically active world in the solar system', false);
INSERT INTO public.moon VALUES (7, 'Titan', 6, 'Saturns largest moon', false);
INSERT INTO public.moon VALUES (8, 'Rhea', 6, 'The second largest moon of Saturn', false);
INSERT INTO public.moon VALUES (9, 'Mimas', 6, 'The smallest and innermost of Saturn', false);
INSERT INTO public.moon VALUES (10, 'Titania', 7, 'The largest moon of Uranus', false);
INSERT INTO public.moon VALUES (11, 'Umbriel', 7, 'The darkest of Uranus largest moons', false);
INSERT INTO public.moon VALUES (12, 'Puck', 7, 'One of the small inner moons of Uranus', false);
INSERT INTO public.moon VALUES (13, 'Triton', 8, 'consists of a crust of frozen nitrogen over an icy mantle', false);
INSERT INTO public.moon VALUES (14, 'Despina', 8, 'Irregularly shaped', false);
INSERT INTO public.moon VALUES (15, 'Nereid', 8, 'One of the outermost of Neptunes moon', false);
INSERT INTO public.moon VALUES (16, 'Proteus', 8, 'One of the largest of Neptunes moon', false);
INSERT INTO public.moon VALUES (17, 'Larissa', 8, 'The fourth-largest satellite of Neptune', false);
INSERT INTO public.moon VALUES (18, 'Charon', 9, 'The largest of Plutos moon and the largest known satellite relative to its parent bod', false);
INSERT INTO public.moon VALUES (19, 'Hydra', 9, 'A natural satellite of Pluto', false);
INSERT INTO public.moon VALUES (20, 'Nix', 9, 'The inner of the two moons discovered orbiting Pluto in 2005', false);


--
-- Data for Name: planet; Type: TABLE DATA; Schema: public; Owner: freecodecamp
--

INSERT INTO public.planet VALUES (1, 'Mercury', 3, 69.10, false);
INSERT INTO public.planet VALUES (2, 'Venus', 5, 107.60, false);
INSERT INTO public.planet VALUES (3, 'Earth', 1, 151.40, true);
INSERT INTO public.planet VALUES (4, 'Mars', 2, 211.40, false);
INSERT INTO public.planet VALUES (5, 'Jupiter', 2, 741.90, false);
INSERT INTO public.planet VALUES (6, 'Saturn', 4, 14742.00, false);
INSERT INTO public.planet VALUES (7, 'Uranus', 6, 29447.00, false);
INSERT INTO public.planet VALUES (8, 'Neptune', 4, 4474.00, false);
INSERT INTO public.planet VALUES (9, 'Pluto', 6, 3700.00, false);
INSERT INTO public.planet VALUES (10, 'Haumea', 1, 6452.00, false);
INSERT INTO public.planet VALUES (11, 'Makemake', 3, 6847.00, false);
INSERT INTO public.planet VALUES (12, 'Eris', 5, 10125.00, false);


--
-- Data for Name: space_rock; Type: TABLE DATA; Schema: public; Owner: freecodecamp
--

INSERT INTO public.space_rock VALUES (1, 'Meteorite', 4.56);
INSERT INTO public.space_rock VALUES (2, 'Iron Meteorite', 2.00);
INSERT INTO public.space_rock VALUES (3, 'Lunar Rocks', 1.97);


--
-- Data for Name: star; Type: TABLE DATA; Schema: public; Owner: freecodecamp
--

INSERT INTO public.star VALUES (1, 'Maia', 1, 126.00, 'Blue');
INSERT INTO public.star VALUES (2, 'Electra', 4, 115.00, 'Blue-white');
INSERT INTO public.star VALUES (3, 'Alcyone', 6, 100.00, 'Blue-white');
INSERT INTO public.star VALUES (4, 'Pleiades', 2, 100.00, 'Hot Blue');
INSERT INTO public.star VALUES (5, 'Alpha Trianguli', 5, NULL, NULL);
INSERT INTO public.star VALUES (6, 'Arcturus', 1, 7105.00, 'Red Giant');


--
-- Name: galaxy_galaxy_id_seq; Type: SEQUENCE SET; Schema: public; Owner: freecodecamp
--

SELECT pg_catalog.setval('public.galaxy_galaxy_id_seq', 1, false);


--
-- Name: moon_moon_id_seq; Type: SEQUENCE SET; Schema: public; Owner: freecodecamp
--

SELECT pg_catalog.setval('public.moon_moon_id_seq', 1, false);


--
-- Name: planet_planet_id_seq; Type: SEQUENCE SET; Schema: public; Owner: freecodecamp
--

SELECT pg_catalog.setval('public.planet_planet_id_seq', 1, false);


--
-- Name: space_rock_space_rock_id_seq; Type: SEQUENCE SET; Schema: public; Owner: freecodecamp
--

SELECT pg_catalog.setval('public.space_rock_space_rock_id_seq', 1, false);


--
-- Name: star_star_id_seq; Type: SEQUENCE SET; Schema: public; Owner: freecodecamp
--

SELECT pg_catalog.setval('public.star_star_id_seq', 1, false);


--
-- Name: galaxy galaxy_name_key; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.galaxy
    ADD CONSTRAINT galaxy_name_key UNIQUE (name);


--
-- Name: galaxy galaxy_pkey; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.galaxy
    ADD CONSTRAINT galaxy_pkey PRIMARY KEY (galaxy_id);


--
-- Name: moon moon_name_key; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.moon
    ADD CONSTRAINT moon_name_key UNIQUE (name);


--
-- Name: moon moon_pkey; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.moon
    ADD CONSTRAINT moon_pkey PRIMARY KEY (moon_id);


--
-- Name: planet planet_name_key; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.planet
    ADD CONSTRAINT planet_name_key UNIQUE (name);


--
-- Name: planet planet_pkey; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.planet
    ADD CONSTRAINT planet_pkey PRIMARY KEY (planet_id);


--
-- Name: space_rock space_rock_name_key; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.space_rock
    ADD CONSTRAINT space_rock_name_key UNIQUE (name);


--
-- Name: space_rock space_rock_pkey; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.space_rock
    ADD CONSTRAINT space_rock_pkey PRIMARY KEY (space_rock_id);


--
-- Name: star star_name_key; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.star
    ADD CONSTRAINT star_name_key UNIQUE (name);


--
-- Name: star star_pkey; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.star
    ADD CONSTRAINT star_pkey PRIMARY KEY (star_id);


--
-- Name: moon moon_planet_id_fkey; Type: FK CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.moon
    ADD CONSTRAINT moon_planet_id_fkey FOREIGN KEY (planet_id) REFERENCES public.planet(planet_id);


--
-- Name: planet planet_star_id_fkey; Type: FK CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.planet
    ADD CONSTRAINT planet_star_id_fkey FOREIGN KEY (star_id) REFERENCES public.star(star_id);


--
-- Name: star star_galaxy_id_fkey; Type: FK CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.star
    ADD CONSTRAINT star_galaxy_id_fkey FOREIGN KEY (galaxy_id) REFERENCES public.galaxy(galaxy_id);


--
-- PostgreSQL database dump complete
--

