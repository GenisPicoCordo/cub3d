# **************************************************************************** #
#                                                                              #
#                                                         :::      ::::::::    #
#    Makefile                                           :+:      :+:    :+:    #
#                                                     +:+ +:+         +:+      #
#    By: gpico-co <gpico-co@student.42.fr>          +#+  +:+       +#+         #
#                                                 +#+#+#+#+#+   +#+            #
#    Created: 2025/05/28 16:32:14 by gpico-co          #+#    #+#              #
#    Updated: 2025/05/28 16:48:25 by gpico-co         ###   ########.fr        #
#                                                                              #
# **************************************************************************** #

NAME := cub3d
CC := cc
CFLAGS := -Wall -Werror -Wextra -g
RM := rm -f

LIBFTDIR := libft
LIBFT := $(LIBFTDIR)/libft.a
MLX42DIR := MLX42
MLX42BUILD := $(MLX42DIR)/build
INCLUDES := -I includes -I $(MLX42DIR)/include -I $(LIBFTDIR)

SRC := src/main/main.c

OBJS := $(SRC:.c=.o)

LIBS := $(MLX42BUILD)/libmlx42.a $(LIBFT) -ldl -lglfw -pthread -lm

all: makelibft libmlx $(NAME)

makelibft:
	make -C $(LIBFTDIR)

libmlx:
	@cmake -DDEBUG=1 $(MLX42DIR) -B $(MLX42BUILD) && make -C $(MLX42BUILD) -j4
	@echo "MLX42 compiled."	

%.o: %.c Makefile includes/cub3d.h
	@$(CC) $(CFLAGS) $(INCLUDES) -c $< -o $@
	@echo "Compiling: $(notdir $<)"

$(NAME): $(OBJS)
	@$(CC) $(OBJS) $(LIBS) -o $(NAME)
	@echo "Final linking: $(NAME) creado."

clean:
	$(RM) -f $(OBJS)
	$(RM) -r $(MLX42BUILD)
	make -C $(LIBFTDIR) clean
	@echo "Object and intermediate compiled files removed."

fclean: clean
	$(RM) $(NAME)
	make -C $(LIBFTDIR) fclean
	@echo "Executables removed."

re: fclean all
	
.PHONY: all clean fclean re libmlx libft